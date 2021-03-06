How to Implement an Entity
==========================

In Elcodi we use an extremely thin model. It means that our entities are just
parameters, getters and setters.

Creating an entity is as easy as defining what an actor should own (parameters),
forgetting about the behavior of this one. This logic will be placed then in the 
service layer.

Let's see a basic implementation of an entity.

``` php
class Product
{
    /**
     * @var name
     *
     * Product name
     */
    protected $name;
     
    /**
     * Get name
     *
     * @return string Product name
     */
    public function getName()
    {
        return $this->name;
    }
    
    /**
     * Set name
     *
     * @param string $name Product name
     *
     * @return $this Self object
     */
    public function setName($name)
    {
        $this->name = $name;
        
        return $this;
    }
}
```

As you can see all properties are defined as protected. This is because Doctrine
will need to extend the class using [transparent Proxy Objects](http://doctrine-orm.readthedocs.org/en/latest/reference/advanced-configuration.html#proxy-objects)
to implement lazy-loading.

### Interfaces

All Elcodi entities are an implementation of a [
Header Interface](http://http://martinfowler.com/bliki/HeaderInterface.html).
We use some 
[Role Interfaces](http://http://martinfowler.com/bliki/RoleInterface.html) in 
our code, but we are more focused in the first one because is more 
understandable for everyone when overriding default implementations.

``` php
use Elcodi\Component\Product\Entity\Interfaces\ProductInterface;

/**
 * Class ProductInterface
 */
class Product implements ProductInterface
{
    // ...
}
```

