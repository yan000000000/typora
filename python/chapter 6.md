# class

## class

### basic syntax

```python
class Computer:
    # constructor (Initialization method)
    def __init__(self, year, brand, cpu, gpu):
        self.year = year
        self.brand = brand
        self.cpu = cpu
        self.gpu = gpu
        self.price = 8800

    def describe(self):
        print(f"This is a {self.brand} {self.year} with {self.cpu}cpu and {self.gpu} pc")

    def get_year(self):
        return self.year

    def substract_price(self, price):
        self.price -= price
        print(f"Current price of this pc is {self.price}")


my_pc = Computer(2020, "Lenovo", "R5800", "RTX3060")
my_pc.describe()
my_pc.substract_price(3000)
```

`__init__` stands for constructor

`self` refer to the class

`self.year` is the internal data

`describe` is the internal function