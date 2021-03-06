# Rails action mailer

## Running this projejct

1. Run `bundle install --path=vendor/bundle` command
1. Run `./bin/rake db:create db:migrate` command
1. Create `config/settings.local.yml` file and edit as shown below:
```yaml
mailer:
  account:
    user_name: 'your gmail user name'
    password: 'your gmail password'
  default:
    from: 'your gmail address'
    to: 'your gmail address'
```
1. Run `./bin/rails s` command
1. Open [localhost:3000](http://localhost:3000/) by your browser
1. Click `Send notification mail` link

## Memo

### ActionMailer minimum settings for GMail

```ruby
config.action_mailer.delivery_method = :smtp
config.action_mailer.smtp_settings = {
  address: 'smtp.gmail.com',
  port: 587,
  authentication: :plain,
  user_name: 'your gmail user name',
  password: 'your gmail password',
}
```

### ActionMailer preview test

This test is existed to confirm mail design. 

If you want to confirm, you need to run Rails server and open [localhost:3000/rails/mailers](http://localhost:3000/rails/mailers) by your browser.

For example:

```ruby
class WelcomeMailerPreview < ActionMailer::Preview
  def notification
    WelcomeMailer.notification
  end
end
```

## See

* [真実は吾にあり: BitnamiのRedmineからのメール送信でエラー(SMTP-AUTH requested but missing secret phrase)](http://blog.sincerity.me/2013/12/bitnamiredminesmtp-auth-requested-but.html)
* [ActionMailer のメール送信テストを RSpec で行う | EasyRamble](http://easyramble.com/test-action-mailer-with-rspec.html)
* [Action Mailer Previews in Ruby on Rails 4.1 - RichOnRails.com](https://richonrails.com/articles/action-mailer-previews-in-ruby-on-rails-4-1)
