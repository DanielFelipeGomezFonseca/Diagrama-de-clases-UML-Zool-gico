```mermaid
---
title: Sistema de Gestión de Zoológico
---
classDiagram
    %% Clases principales
    class Zoologico {
        +nombre: String
        +ubicacion: String
        +agregarAnimal(a: Animal): void
        +asignarCuidador(c: Cuidador): void
        +realizarRevisionMedica(): void
    }

    class Habitat {
        +id: int
        +tipo: String
        +clima: String
        +agregarAnimal(a: Animal): void
    }

    class Animal {
        +nombre: String
        +edad: int
        +especie: String
        +genero: String
        +hacerSonido(): void
        +comer(alimento: Alimento): void
    }

    %% Subclases de Animal
    class Mamifero {
        +tienePelo: bool
        +tipoReproduccion: String
    }

    class Ave {
        +puedeVolar: bool
        +tipoPico: String
    }

    class Reptil {
        +esVenenoso: bool
        +tipoEscamas: String
    }

    %% Relaciones de herencia
    Mamifero --|> Animal
    Ave --|> Animal
    Reptil --|> Animal

    %% Cuidador y Veterinario
    class Cuidador {
        +nombre: String
        +id: int
        +especialidad: String
        +alimentarAnimales(): void
    }

    class Veterinario {
        +nombre: String
        +id: int
        +realizarRevision(a: Animal): void
        +administrarMedicamento(a: Animal, medicamento: String): void
    }

    class Alimento {
        +nombre: String
        +tipo: String
        +cantidad: float
    }

    %% Relaciones
    Zoologico "1" --> "*" Habitat : contiene
    Habitat "1" --> "*" Animal : contiene
    Zoologico "1" --> "*" Cuidador : emplea
    Zoologico "1" --> "*" Veterinario : emplea
    Cuidador "1" --> "*" Animal : cuida
    Veterinario "1" --> "*" Animal : atiende
    Animal "1" --> "*" Alimento : come
