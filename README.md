# How to Write Clean Code

I don't want to reiterate the common advice found in other documents or articles about choosing declarative variable names, using good method names, etc. While these are fundamental for writing clean code, I want to add a bit of extra polish to make it perfect.

## Feel Good About Your Code

First and foremost, if you're writing, developing, or maintaining a project and you don't feel good about it, there's something right with clean code. This indicates that you should change something, gain more knowledge in the clean code industry, and write code in a way that you enjoy. As developers, we spend most of our time coding, so it's crucial to enjoy it.

## Gaining Knowledge

There are thousands of documents and books available that are very helpful, such as "Clean Code" by Robert C. Martin. We should gain a lot of knowledge in clean coding practices. Each programming language and framework has its own best practices. The more knowledge we gain, the better we can code. However, it's not necessary to implement all best practices. By practicing and writing a lot of code, we gain the experience to decide which practices are best to use and even develop our own style.

## Reading and Revising Your Code

After writing, put yourself in another person's shoes and read your code. For example, consider a function named `prepareDataBeforeSending()`. The name indicates that it prepares data before sending it somewhere. By inspecting your code like this, you'll become more careful about your code. Initially, this might seem scary because it can slow down your performance, but with practice, it becomes second nature.

The more I read my code, the more mistakes I find. For example, my code after being written and then inspected twice is completely different. The final version is much simpler, easier to understand, and performs better because I can find duplicate queries or unnecessary parameters being passed to functions.

## Start from the End

Starting from the end is a cool thing. Let me explain it more: for example, you need to write a function that gets all data where `end_date` in the database is less than today and then makes several API calls to third parties. Instead of writing a long method or code, I'd prefer to divide it into two functions. Why? Because logically, we need to first fetch data and then do something with it.

Here's a Laravel code example:

```php
public function handle(): void
{
    $data = $this->fetchData();

    $this->makeApis($data);
}
```

Then I'll create those methods. It would be something like Test-Driven Development (TDD) style: we first write something that we know does not exist, then we'll make it. In this part, we are somehow doing the same. We are making the code as we want it to be when we look at it, then we'll implement it as we want. We can even do it recursively.

For example, making APIs might need several things. We can do something like this:
```php
private function makeApis(array $data)
{
    $contractors = Contractor::getActive();

    array_map(
		fn (CallableInterface $contract) => $contract->call(),
		$contractors
	);
}
```
As you can see, we are creating the code as we want it. So, I need a Contractor class with a static method to do some logic.

Starting from the end, personally, I find this method to write clean code very helpful.

## Make it Short
Make everything as simple and short as possible. If you are writing a method, make it as small as possible. If you are creating a class, make it as small as possible. Ensure everything does one thing and is reusable in other parts of the code. This approach is very helpful.

Additionally, format folder structures well. They should be clean, descriptive, and simple, adhering to the conventions of the language or framework. Modular programming is great for this purpose.

## Continuous Learning
Like Gaining Knowledge I said earlier we should update ourselves constantly. We should gain knowledge every day, read others' code, read articles, learn from others' mistakes, or AI, but it should be constantly ...

In conclusion, I wanted to make this document different from other documents out there. Those documents are great for learning clean code, but I wanted to emphasize that enjoying coding is essential. If not, we should change something.

## Enjoy coding!


