# Schedule DSL



The convenience methods merely wrap properties of the [AWS::Events::Rule](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-events-rule.html#cfn-events-rule-description).  If you wanted to set the CloudFormation properties more directly, here's an example of using the "Full" DSL.

.codebuild/schedule.rb:

```ruby
description "my description"
schedule_expression "rate(1 day)"
```