## Code Smell 03 - Long Methods

### Introduction

What is a lengthy method, first of all? What does "LONG" actually mean? How much time is too much? (5) Lines? Definitely not. Twenty? I suppose not. Forty? Probably, I suppose. Eighty? almost certainly However, there is never a strict rule that applies to code smells; there are always exceptions.

### TL;DR:
Refactor and extract functions longer than 10 lines.

### Signs and Symptoms
1. A method contains too many lines of code. Generally, any method longer than ten lines should make you start asking questions.

2. As a rule of thumb, if you feel the need to comment on something inside a method, you should take this code and put it in a new method. Even a single line can and should be split off into a separate method, if it requires explanations. And if the method has a descriptive name, nobody will need to look at the code to see what it does.

3. There is no defined length of lines for the code. Mostly a method with not more than 10 lines is recommended. Think of it like adding salt to noodles. It's hard to describe what "too much" is in tea spoon, but you'll know it when you taste it. 

### More Light on Long Method

What is the long method code smell? It’s about as simple as it sounds: it’s just a method which includes many lines of code. Exactly how long is too long is debatable and somewhat dependent on language. For instance Sandi Metz argues in her rules for developers that methods should be no more than five lines long. Some prefer methods that are nearly always just one line.


### Problems 

- **The code is hard to read**. Code is read far more often than it is produced, thus taking the extra time to condense a method might have significant benefits. In order to properly make a change in a lengthy process, you must study and comprehend every line of code. In order to grasp what is happening in this example, much alone be able to alter any aspect of it, we must mentally process all the work that this technique is performing.

- **Breaking the Single Responsibility Princicple**. The code is doing more than one thing. Single Responsibility Principle, a method should really only do one thing. It’s nearly impossible to only do one thing in that many lines of code.

- **It makes the code hard to maintain.**. If the code is having more lines, then we need to spend extra time figuring out what this method does, which makes me not want to touch it in the first place, which means code like this is going to tend to go stale.

- **Makes code hard to test** and that erodes my confidence that I can change it without unknowingly breaking something. Code tends to attract more of the same design patterns (or anti-patterns) already present in it, so future me is much more likely to just continue dumping logic into this method since that’s “faster” than refactoring it and it seems less risky in the short term. Methods like this turn into bigger messes over time.

- **Duplication of Code**. There might be duplicate code. When we have a small number of methods with distinct names, finding duplication is much simpler. If I ever need to obtain the date from 30 days ago again, I'll probably just wind up developing code that accomplishes the same task someplace else somewhat differently.

- **Attract other code smells**. You can see that I've begun grouping the code into sections in this example. That fragrance is truly its own, and it organically develops as the procedure becomes longer and more intricate. A great name makes the best remark.


### Explanation

Consider the below code, 

```
import time

def send_mail_alerts_to_participants_who_are_active(mails):
	
	active_mails = []
	# List of users who are active
	for mail in mails:
		if mail.is_active():
			active_mails.append(mail)
	
	# Create mail content
	mail_content = "Hi subscriber's , Thanks for being with us."
	
	# Send mail to users
	for mail in active_mails:
		try:
			mail.send()
		except Exception as ex:
			print(str(ex))	 
```

Our function name is 'send_mail_alerts_to_participants_who_are_active'; so we presume that’s what it’s doing, but under the hood it’s doing many things.
In the above code, we are doing many executions like collecting emails, creating mail content, and sending mail to the user. That’s a lot of work for one method or function.

**It makes the code hard to maintain.**. If the code is having more lines, then we need to spend extra time figuring out what this method does, which makes me not want to touch it in the first place, which means code like this is going to tend to go stale.


### How to fix ?


When determining if a code smell has to be refactored, a few factors should be considered. 
- The method's complexity is the first factor.
- The more loops and branches a method contains, the longer it is, the worse it is. 
- You can certainly put up with a lengthier method if it largely consists of highly scannable code, such configuration, text, HTML, or object/data definitions.

By applying the refactoring strategies, we can achieve the following code, 

```
import time

def get_active_mails():
	active_mails = []
	for mail in mails:
		if mail.is_active():
			active_mails.append(mail)
	return active_mails

def get_mail_content():
	mail_content = "Hi subscriber's , Thanks for being with us."
	return mail_content

def send_mail(mails):
	for mail in mails:
		try:
			mail.send()
		except Exception as ex:
			print(str(ex))

def send_mails_to_active_participants():
	active_mails = get_active_mails()
	mail_content = get_mail_content()
	send_mail(active_mails)


```

Now the above code is of more clear, easy to understand. Since we have many small methods. Its easy to maintain, more readable. 

#### Refactoring Methods

There are a few ways to simplify long methods, 

1. Usage of Extract Method.
2. Pull out those chunks of code and lines that looks like they are working closely together into their own methods.
3. Give them good, clear names and reference them back in the spot you extracted them out of. 
4. If you have a lot of local variables making method extraction difficult, you might have a new object trying to get out.

### Will increase in number of methods affect performance ?

In almost all cases the impact is so negligible that it’s not even worth worrying about. After refactoring, you will have clear and understandable code, you’re more likely to find truly effective methods for restructuring code and getting real performance gains if the need ever arises.


### Benefits

1. Among all types of object-oriented code, classes with short methods live longest.
2. Less duplication of code.
3. In order to resolve long methods, we usually have to create more methods. Those methods have names. Those names give us better descriptions of what our code is doing. We get a better abstraction of our code that is easier to understand at our current abstraction level.

### Final Thoughts
This will be a time intensive process. A method might be on the verge of getting affected by this code smell. But we have to be diligent, and we have to train ourselves on what to look for. And we also have to lower our tolerance to just "fix it later".










