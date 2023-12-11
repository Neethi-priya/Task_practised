# 1. class circle, constructor, private variable, class methods 

`
class Circle:
    
    __pi = 3.14
    def __init__(self,list_1):
        self.list_1 = list_1 
    
    def area_of_circle(self):
        area = [self.__pi*r*r for r in self.list_1]
        return area
    
    def perimeter_of_circle(self):
        perimeter = [2*self.__pi*r for r in self.list_1]
        return perimeter
    
user_list = [int(number) for number in input("Enter the list_1: ").split()]
circle_obj = Circle(user_list)
print("Area's: ", circle_obj.area_of_circle())
print("Perimeter's: ", circle_obj.perimeter_of_circle()) 

`
# class methods

`
class Circle:
    
    __pi = 3.14
    def __init__(self,list_1):
        self.list_1 = list_1 
    
    @classmethod
    def area_of_circle(cls):
        area = [cls.__pi*r*r for r in user_list]
        return area
    
    @classmethod
    def perimeter_of_circle(cls):
        perimeter = [2*cls.__pi*r for r in user_list]
        return perimeter
    
user_list = [int(number) for number in input("Enter the list_1: ").split()]
Circle(user_list)
print("Area's: ", Circle.area_of_circle())
print("Perimeter's: ", Circle.perimeter_of_circle())


`

# 2. Ques no 4

`
class TV:
    def __init__(self, brand):
        self.brand = brand
        self.default_channel = 1
        self.default_volume = 50
        self.inches = 49
        self.on = False
        self.volume = 75 
        self.channel = 8
        
    def increase_volume(self):
        if self.volume > 100:
            self.volume -= 1
                    
    def decrease_volume(self):
        if self.volume <= 0:
            self.volume += 1
            
    def set_channel(self):
        if 1 <= self.channel <= 50:
            return self.channel
        else:
            return self.default_channel
            
    def reset_tv(self):
        self.channel = 1
        self.volume = 50
        
    def get_status(self):
        return f"{self.brand} at channel {self.set_channel()}, volume {self.volume}"
    
    
class LedTV(TV):
    
    def __init__(self, brand, screen_thickness, energy_usage, lifespan, refresh_rate):
        super().__init__(brand)
        self.screen_thickness = screen_thickness
        self.energy_usage = energy_usage
        self.lifespan = lifespan
        self.refresh_rate = refresh_rate
        
    def display_details(self):
        return f"{self.get_status()}, Screen Thickness: {self.screen_thickness}, Energy Usage: {self.energy_usage},Lifespan: {self.lifespan}, Refresh Rate: {self.refresh_rate}"
               

class PlasmaTV(TV):
    
    def __init__(self, brand, screen_thickness, energy_usage, lifespan, viewing_angle, backlight):
        super().__init__(brand)
        self.screen_thickness = screen_thickness
        self.energy_usage = energy_usage
        self.lifespan = lifespan
        self.viewing_angle = viewing_angle
        self.backlight = backlight
        
    def display_details(self):
        return f"{self.get_status()}, Screen Thickness: {self.screen_thickness}, Energy Usage: {self.energy_usage},Lifespan: {self.lifespan}"
    
led_tv = LedTV("panasonic","Slim", "Low", "8 years", "120Hz")
plasma_tv = PlasmaTV("Sony", "Slim", "Medium", "11 years", "180 degrees", "LED")
tv = led_tv.get_status()
print(tv)
print(led_tv.display_details())
print(plasma_tv.display_details())


`