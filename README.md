# Dripper

Clean up your mailer code with a rules-based drip campaign system that works natively with rails

## Simple Stuff
```
dripper :users do 
  # send a welcome message
  message :welcome_mailer, :welcome
end

dripper :orders do
  # send a successful order message
  message :order_mailer, :new_order, { paid }
end
```

## Drip Stuff
Drip messages are designed to get people to take specific actions based on their lifecycle

### Inactive User
```
# define inactive scope
class User 
  scope :inactive, -> { where("last_session_at < ?", DateTime.today - 1.months) }
end

# dripper code uses scope
dripper :users do
  message :user_mailer, :inactive, { inactive }
end
```

This project rocks and uses MIT-LICENSE.