## Tips for Conducting a Code Review
### Use a code linter
Using a Python code linter like [pylint](https://www.pylint.org/) can automatically check for coding standards.
### Explain issues and make suggestions
BAD: Make model evaluation code its own module - too repetitive.

BETTER: Make the model evaluation code its own module. This will simplify models.py to be less repetitive and focus primarily on building models.

GOOD: How about we consider making the model evaluation code its own module? 
This would simplify models.py to only include code for building models. 
Organizing these evaluations methods into separate functions would also allow us to reuse them with different models without repeating code.
### Keep your comments objective
BAD: I wouldn't groupby genre twice like you did here... Just compute it once and use that for your aggregations.

BAD: You create this groupby dataframe twice here. 
Just compute it once, save it as groupby_genre and then use that to get your average prices and views.

GOOD: Can we group by genre at the beginning of the function and then save that as a groupby object? 
We could then reference that object to get the average prices and views without computing groupby twice.

### Provide code examples
BAD: You can do this all in one step by using the pandas str.split method.

GOOD: We can actually simplify this step to the line below using the pandas str.split method. 
Found this on this [stack overflow post](https://stackoverflow.com/questions/14745022/how-to-split-a-column-into-two-columns).

df['first_name'], df['last_name'] = df['name'].str.split(' ', 1).str
