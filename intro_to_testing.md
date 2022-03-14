### Setup
```
gem install rspec
```
| [Core Docs](https://rspec.info/documentation/3.9/rspec-core/RSpec/Core/Configuration) | [Expects Docs](https://www.rubydoc.info/github/rspec/rspec-expectations/RSpec/Expectations) |

### RSpec Req Dir Structure
- ClassMy implies self: lib/classmy.rb & spec/classmy_spec.rb [require './lib/classmy']
```
. (RSpec cmd here... or rspec spec/goblins_spec.rb singleton)
├── lib
|   └── goblins.rb
└── spec
    └── goblins_spec.rb 
```
### Code-Along Scenario

```ruby
pry(main)> require './lib/stu' => true
pry(main)> stu = Stu.new('Sam') => <Stu:f0 @cookies=[], @name='Sam'>
pry(main)> stu.name => 'Sam'
pry(main)> stu.cookies => []
pry(main)> stu.add_cookie('Chocolate Chip')
pry(main)> stu.cookies => ['Chocolate Chip']
```
Write test:

```ruby
require 'rspec'                        # Run test, code:               # Test Refactor
require './lib/stud'                                                                                                 
describe Stu do                          class Stu                       describe Stu do
  describe '#initialize' do              end                               before(:each) do
    it 'is an instance of student' do                                        @stu = Stu.new('Sam')
      stu = Stu.new('Sam')                                                 end
      expect(stu).to be_a Stu          # Repeat test (assert):             
    end                                                                    describe '#initialize' do
                                         it 'has a name' do                  it 'is an instance of a student' do
                                           stu = Stu.new('Sam')                expect(stu).to be_a Stu
  end                                      expect(stu.name).to eq 'Sam'      end
end                                      end                                 it 'has a name' do
                                                                               expect(stu.name).to eq 'Sam'
                                                                             end
                                                                           end
                                                                         end
      
      
      
                                    # be true # be_nil # include # be_empty
                                          # expect(any).to eq(anyelse)
                                                                                       
```
Code: 

```ruby

class Stu              # Write test '#initialize':                                # Dynamic (sorta) Assert '#initialize':
  attr_reader :name                                        
                             it 'has cookies by default' do                         it 'has a different name' do                              
  def initialize(name)         expect(stu.cookies).to eq []                           stu = Stu.new('James')
    @name = name             end                                                       expect(stu.name).to eq 'James'
  end                                             
end                        # Pass with attr_r:                                     # Edge Case Assert '#initialize':                             
                             @cookies = cookies
                                                                                     it 'assigns default name' do
                           # Write test '#add_cookie':                                 stu = Stu.new(42)
                                                                                         expect(stu.name).to eq 'DefaultName'
                             describe '#add_cookie' do                                 end
                               it 'provide Student instances with cookies' do              
                                 stu.add_cookie('Chocolate Chip')
                                 expect(stu.cookies).to eq ['Chocolate Chip']
                               end
                             end                     
 ```
 
