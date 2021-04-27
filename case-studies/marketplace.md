# Marketplace

```
#TODO:
# - approval (a shop can start operation after it has been approved)
# - tier (a paying shop gets more features)
entity Shop {
  id {
    prefix MSh

    # ...
  }
  
  creation {
    # ...
  }

  # - A shop ownership could be transferred
  # - A shop has at least one owner but no more than two owners
  ownership {
    transfer enabled {
      #TODO: rules. does it need verification?
    }

    owner_arity 1..2
  }
  
  attributes {
    DisplayName: thing.Name {
      #TODO: rules like how frequent the name can be changed, the length constraints, who can change the name, etc.
    }
    
    # ...
  }
  
  # ...
}

# - A shop could have more than one managers but no more than three managers
# - A user could manage more than one shops
adjunct Manager {
  hosts {
    Shop
    iam.User {
      #TODO: find a clearer way to express the rule.
      # this is potentially confusing on where the arity constraint is in relation to, to the adjunct or to the other hosts.
      arity 1..3
    }
  }
  
  # ...
}

adjunct entity Article {
  hosts {
    Shop
  }
  
  id {
    prefix MAr

    # ...
  }
  
  attributes {
    DisplayName: thing.Name
    Images: set {
        #TODO: constraints for the 'set', e.g., min max
      } of media.Image {
        #TODO: constraints for the 'media.Image', e.g., max size in bytes
      }
    
    # ...
  }
  
  # ...
}

# - Showcase or section?
adjunct entity Showcase {
  hosts {
    Shop
  }
  
  id {
    # ...
  }
  
  #TODO: articles
  
  # ...
}

adjunct Cart {
  hosts {
    iam.User {
      arity 1
    }
  }
  
  #TODO: items
  
  # ...
}

# ...

```
