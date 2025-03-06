import pickle


# Базовый класс Animal
class Animal:
    def __init__(self, name, age):
        self._name = name
        self._age = age

    def make_sound(self):
        raise NotImplementedError("This method should be overridden in subclasses")

    def eat(self):
        print(f"{self._name} is eating.")


# Подкласс Bird
class Bird(Animal):
    def __init__(self, name, age, wing_span):
        super().__init__(name, age)
        self._wing_span = wing_span

    def make_sound(self):
        print(f"{self._name} chirps.")


# Подкласс Mammal
class Mammal(Animal):
    def __init__(self, name, age, fur_color):
        super().__init__(name, age)
        self._fur_color = fur_color

    def make_sound(self):
        print(f"{self._name} roars.")


# Подкласс Reptile
class Reptile(Animal):
    def __init__(self, name, age, scale_type):
        super().__init__(name, age)
        self._scale_type = scale_type

    def make_sound(self):
        print(f"{self._name} hisses.")


# Функция для демонстрации полиморфизма
def animal_sound(animals):
    for animal in animals:
        animal.make_sound()


# Класс Zoo
class Zoo:
    def __init__(self):
        self._animals = []
        self._staff = []

    def add_animal(self, animal):
        self._animals.append(animal)

    def add_staff(self, staff_member):
        self._staff.append(staff_member)

    def get_animals(self):
        return self._animals

    def get_staff(self):
        return self._staff

    def save_to_file(self, filename):
        with open(filename, 'wb') as file:
           pickle.dump(self, file)

    @staticmethod
    def load_from_file(filename):
        with open(filename, 'rb') as file:
            return pickle.load(file)


# Класс ZooKeeper
class ZooKeeper:
    def __init__(self, name):
        self._name = name

    def feed_animal(self, animal):
        print(f"{self._name} is feeding {animal._name}.")


# Класс Veterinarian
class Veterinarian:
    def __init__(self, name):
        self._name = name

    def heal_animal(self, animal):
        print(f"{self._name} is healing {animal._name}.")


# Пример использования
if __name__ == "__main__":
    # Создаем зоопарк
    zoo = Zoo()

    # Создаем животных
    parrot = Bird(" Parrot ", 2, "Medium ")
    lion = Mammal("Lion", 5, "Golden")
    snake = Reptile("Snake", 3, "Smooth")

    # Добавляем животных в зоопарк
    zoo.add_animal(parrot)
    zoo.add_animal(lion)
    zoo.add_animal(snake)

    # Создаем сотрудников
    keeper = ZooKeeper("John")
    vet = Veterinarian("Dr. Smith")

    # Добавляем сотрудников в зоопарк
    zoo.add_staff(keeper)
    zoo.add_staff(vet)

    # Демонстрируем полиморфизм
    animals = zoo.get_animals()
    animal_sound(animals)

    # Сотрудники взаимодействуют с животными
    keeper.feed_animal(lion)
    vet.heal_animal(snake)

    # Сохраняем данные зоопарка в файл
    zoo.save_to_file("zoo_data.pkl")

    # Загружаем данные зоопарка из файла
    loaded_zoo = Zoo.load_from_file("zoo_data.pkl")
    print("\nLoaded Zoo Data:")
    for animal in loaded_zoo.get_animals():
        print(f"Animal: {animal._name}, Age: {animal._age}")
