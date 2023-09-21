# CPP

### Adopt a case convention for each semantic category and stick to it project-wide
Some of the more widely spreaded case convention are:
- **s**nake**\_c**ase
- **c**amel**C**ase
- **P**ascal**C**ase

exemple:
```
class MyClass {
    public:
        void myMethod(void);
    private:
        int _my_attribute;
};
```

### Name things by short names reflecting their purpose
exemple:
```
#include <regex>
int main(void)
{
    std::regex re("[0-9a-zA-Z]");
    [...]
    return (0);
}
```

### Containers
When iterating through a [Contiguous Container](https://en.cppreference.com/w/cpp/named_req/ContiguousContainer), use the container dedicated iterator rather than direct access to elements through their index.
It makes the process more consistent with the treatement implying containers that does not permit the 2nd.
Moreover, it makes the process of changing the underlying container transparent.

### Loops

- `for`
    - when the number of iterations is size-linear
        ```
        #include <vector>
        int main(void)
        {
        	std::vector<char> letters{'a', 'b', 'c'};
        	for (std::vector<char>::const_iterator it = letters.begin(); it != letters.end(); ++it)
        	{
        		[...]
        	}
        	[...]
        	return (0);
        }
        ```
- `while`
    - otherwhise
        ```
        #include <vector>
        int main(void)
        {
        	std::vector<char> letters{'a', 'b', 'c'};
        	std::vector<char>::const_iterator it_letters = letters.begin();
        	while (it_letters != letters.end() && *it_letters != 'b')
        	{
        		[...]
        		++it_letters;
        	}
        	[...]
        	return (0);
        }
        ```
- `break`
    - I highly recommend to stick it to `switch`/`case` statements
- `continue`
    - I recommend not to use it at all

### Class implementation

- A method that does not interact with the attributes of its belonging class should be declared as `static`
- Avoid singleton pattern
