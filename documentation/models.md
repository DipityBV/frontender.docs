---
currentMenu: models
---

# Adapters

An adapter is basically a collection (directory) of models that belong together.
This only has impact on the namespace of a model.

# Models

### What

The models are the part of the platform that will communicate with the datastore.
The models also hold all the information required to connect an retrieve data from the datastore.

### Basics

After we have created an adapter directory we will place the models in there.
The naming convention is as follows: `<AdapteName>/<ModelName>Model.php`. eg: `Contentful\EntityModel.php`.

The first thing we need to define in a odel is the namespace.
The namespases are based on [PSR-4 autoloading standard](https://www.php-fig.org/psr/psr-4/) with a base namespace of `Frontender\Platform`. eg: `Frontender\Platform\Contentful\EntityModel`.

<!-- Due to the fact that FEP will most likely be encrypted I have added the class names -->

Each model must extend from `Frontender\Core\Model\AbstractModel`,
this model will add all variables that we use in the rest of the core and which other users can also use.

Also each model must have a fetch method that will retrieve the data from the datastore of their chosing.

Example:

```php
namespace Frontender\Platform\Contentful\EntityModel;

use Frontender\Core\Model\AbstractModel;
use Slim\Container;

class EntityModel extends AbstractModel
{
    public function __construct(Container $container)
    {
        parent::__construct($container);

        $this->getState()
            ->insert('id'); // Each model that also returns single items MUST have an id state.

        $this->adapter = '<connection to contentful>';
    }

    public function fetch(): array // Each fetch method MUST return an array of model instances.
    {
        $id = $this->getState()->id ?? false;

        if($id) {
            return $this->adapter->fetchEntity($id);
        }

        return $this->adapter->fetchEntities();
    }

    /**
     * This is a method that is called when using $model->headline.
     * Once the value is found the data is cached for future use.
     */
    public function getPropertyHeadline(): string
    {
        return 'custom method to get the headline of an entity';
    }
}
```
