---
title: Obliczone i niestandardowe właściwości przechowywania
description: Dowiedz się, w jaki sposób wszystkie właściwości domeny w języku specyficznym dla domeny (DSL) mogą być wyświetlane użytkownikowi na diagramie i w Eksploratorze języka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c50d205745917b3af7de638a17921f4bcdca509
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363552"
---
# <a name="calculated-and-custom-storage-properties"></a>Obliczone i niestandardowe właściwości przechowywania
Wszystkie właściwości domeny w języku specyficznym dla domeny (DSL) mogą być wyświetlane użytkownikowi na diagramie i w Eksploratorze języka, a dostęp do niego można uzyskać za pomocą kodu programu. Jednak właściwości różnią się w sposób, w jaki są przechowywane ich wartości.

## <a name="kinds-of-domain-properties"></a>Rodzaje właściwości domeny
 W definicji DSL można ustawić **rodzaj** właściwości domeny, jak opisano w poniższej tabeli:

|Rodzaj właściwości domeny|Opis|
|-|-|
|**Standardowa** (domyślnie)|Właściwość domeny, która jest zapisywana w *magazynie* i serializowana do pliku.|
|**Obliczeniowy**|Właściwość domeny tylko do odczytu, która nie jest zapisywana w sklepie, ale jest obliczana na podstawie innych wartości.<br /><br /> Na przykład `Person.Age` można obliczyć z `Person.BirthDate` .<br /><br /> Musisz podać kod, który wykonuje obliczenia. Zwykle oblicza się wartość z innych właściwości domeny. Można jednak również używać zasobów zewnętrznych.|
|**Magazyn niestandardowy**|Właściwość domeny, która nie jest zapisywana bezpośrednio w magazynie, ale może być zarówno Get, jak i Set.<br /><br /> Musisz podać metody pobierające i ustawiające wartość.<br /><br /> Na przykład `Person.FullAddress` może być przechowywana w `Person.StreetAddress` , `Person.City` , i `Person.PostalCode` .<br /><br /> Możesz również uzyskać dostęp do zasobów zewnętrznych, na przykład w celu pobrania i ustawienia wartości z bazy danych.<br /><br /> Kod nie powinien określać wartości w magazynie, gdy `Store.InUndoRedoOrRollback` ma wartość true. Zobacz [transakcje i niestandardowe metody ustawiające](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Dostarczanie kodu dla właściwości magazynu obliczeniowego lub niestandardowego
 W przypadku ustawienia rodzaju właściwości domeny na obliczeniową lub niestandardową magazyn należy zapewnić metody dostępu. Podczas kompilowania rozwiązania raport o błędach informuje o tym, co jest wymagane.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Aby zdefiniować obliczoną lub niestandardową Właściwość magazynu

1. W DslDefinition. DSL wybierz właściwość domeny na diagramie lub w **Eksploratorze DSL**.

2. W oknie **Właściwości** ustaw wartość pola **rodzaj** na **obliczeniowy** lub **niestandardowy magazyn**.

     Upewnij się, że ustawiono również jego **Typ** w żądany sposób.

3. Kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi **Eksplorator rozwiązań**.

4. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Zostanie wyświetlony następujący komunikat o błędzie: "*YourClass* nie zawiera definicji dla get *YourProperty*".

5. Kliknij dwukrotnie komunikat o błędzie.

     Zostanie otwarty Dsl\GeneratedCode\DomainClasses.cs lub DomainRelationships.cs. Nad wyróżnionym wywołaniem metody komentarz jest monitowany o podanie implementacji dla get *YourProperty*().

    > [!NOTE]
    > Ten plik jest generowany z DslDefinition. DSL. Jeśli edytujesz ten plik, zmiany zostaną utracone przy następnym kliknięciu pozycji **Przekształć wszystkie szablony**. Zamiast tego należy dodać wymaganą metodę w oddzielnym pliku.

6. Utwórz lub Otwórz plik klasy w oddzielnym folderze, na przykład atrybut CustomCode \\ *YourDomainClass*. cs.

     Upewnij się, że przestrzeń nazw jest taka sama jak w wygenerowanym kodzie.

7. W pliku klasy Napisz częściową implementację klasy domeny. W klasie Napisz definicję brakującej `Get` metody podobnej do poniższego przykładu:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. W przypadku ustawienia **rodzaju** na **Magazyn niestandardowy** należy również podać `Set` metodę. Na przykład:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Kod nie powinien określać wartości w magazynie, gdy `Store.InUndoRedoOrRollback` ma wartość true. Zobacz [transakcje i niestandardowe metody ustawiające](#setters).

9. Skompiluj i uruchom rozwiązanie.

10. Przetestuj właściwość. Upewnij się, że próbujesz **cofnąć** i **ponownie** wykonać operację.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transakcje i niestandardowe metody ustawiające
 W metodzie Set niestandardowej właściwości magazynu nie trzeba otwierać transakcji, ponieważ metoda jest zwykle wywoływana wewnątrz aktywnej transakcji.

 Jednak Metoda set może być również wywoływana, jeśli użytkownik wywołuje polecenie Cofnij lub Ponów, lub jeśli transakcja jest wycofywana. Gdy <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> ma wartość true, Metoda Set powinna zachowywać się w następujący sposób:

- Nie należy wprowadzać zmian w magazynie, na przykład przypisywania wartości do innych właściwości domeny. Menedżer cofania ustawi wartości.

- Należy jednak zaktualizować wszystkie zasoby zewnętrzne, takie jak baza danych lub zawartość pliku, lub obiekty spoza magazynu. Dzięki temu dane będą przechowywane w synchronism z wartościami w sklepie.

  Na przykład:

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 Aby uzyskać więcej informacji na temat transakcji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Właściwości właściwości domeny](../modeling/properties-of-domain-properties.md)
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
