# Ruby Cheatsheet

## Basics
```ruby
puts "Hello, World!" # Print to console
name = "Alpha" # Variable assignment
age = 25 # Integer
pi = 3.14 # Float
is_active = true # Boolean
```

## Data Types
```ruby
string = "Hello"
integer = 42
float = 3.14
boolean = true
array = [1, 2, 3, "four"]
hash = { name: "Alpha", age: 25 }
nil_value = nil
```

## Conditionals
```ruby
if age >= 18
  puts "Adult"
elsif age >= 13
  puts "Teenager"
else
  puts "Child"
end

# Ternary Operator
puts age >= 18 ? "Adult" : "Minor"
```

## Loops
```ruby
# While loop
x = 0
while x < 5
  puts x
  x += 1
end

# For loop
for i in 1..5 do
  puts i
end

# Each loop (for arrays)
["Apple", "Banana", "Cherry"].each do |fruit|
  puts fruit
end
```

## Methods
```ruby
def greet(name)
  "Hello, #{name}!"
end

puts greet("Alpha")
```

## Classes & Objects
```ruby
class Person
  attr_accessor :name, :age

  def initialize(name, age)
    @name = name
    @age = age
  end

  def introduce
    "Hi, I'm #{@name} and I'm #{@age} years old."
  end
end

alpha = Person.new("Alpha", 25)
puts alpha.introduce
```

## Modules
```ruby
module Greetings
  def say_hello
    "Hello!"
  end
end

class User
  include Greetings
end

user = User.new
puts user.say_hello
```

## File Handling
```ruby
# Writing to a file
File.open("test.txt", "w") { |file| file.puts "Hello, File!" }

# Reading a file
content = File.read("test.txt")
puts content
```

## Exception Handling
```ruby
begin
  result = 10 / 0
rescue ZeroDivisionError => e
  puts "Error: #{e.message}"
end
```

## Useful Methods
```ruby
# String Manipulation
"hello".upcase # "HELLO"
"WORLD".downcase # "world"
"ruby".capitalize # "Ruby"

# Array Methods
array = [1, 2, 3, 4, 5]
array.push(6) # Add element
array.pop # Remove last element
array.each { |num| puts num * 2 }

# Hash Methods
hash = { name: "Alpha", age: 25 }
hash[:city] = "Joburg" # Add key-value pair
puts hash.keys # [:name, :age, :city]
puts hash.values # ["Alpha", 25, "Joburg"]
```

## Blocks, Procs & Lambdas
```ruby
# Block
[1, 2, 3].each { |num| puts num * 2 }

# Proc
square = Proc.new { |num| num ** 2 }
puts square.call(4) # 16

# Lambda
cube = ->(num) { num ** 3 }
puts cube.call(3) # 27
```

## Metaprogramming
```ruby
class DynamicClass
  define_method(:dynamic_method) { "This is dynamic!" }
end

dc = DynamicClass.new
puts dc.dynamic_method
```

## Working with Gems
```ruby
# Install a gem
# gem install nokogiri

# Using a gem
require 'nokogiri'
```

## HTTP Requests
```ruby
require 'net/http'
require 'json'

url = "https://jsonplaceholder.typicode.com/posts/1"
response = Net::HTTP.get(URI(url))
puts JSON.parse(response)
```

## Threads & Concurrency
```ruby
threads = []
5.times do |i|
  threads << Thread.new { puts "Thread #{i} is running" }
end
threads.each(&:join)
```

## Database (SQLite)
```ruby
require 'sqlite3'

db = SQLite3::Database.new "test.db"
db.execute "CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT)"
db.execute "INSERT INTO users (name) VALUES ('Alpha')"
db.execute( "SELECT * FROM users" ) do |row|
  puts row.join(" ")
end
```
