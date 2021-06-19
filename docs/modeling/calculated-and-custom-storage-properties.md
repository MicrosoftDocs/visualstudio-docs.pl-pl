---
title: Obliczone i niestandardowe właściwości przechowywania
description: Dowiedz się, jak wszystkie właściwości domeny w języku specyficznym dla domeny (DSL) mogą być wyświetlane użytkownikowi na diagramie i w Eksploratorze języka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98dca6759b9e4a77e71139b6d9ec9b394d99b04
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385425"
---
# <a name="calculated-and-custom-storage-properties"></a>Obliczone i niestandardowe właściwości przechowywania
Wszystkie właściwości domeny w języku specyficznym dla domeny (DSL) mogą być wyświetlane użytkownikowi na diagramie i w Eksploratorze języka i można uzyskać do nich dostęp za pomocą kodu programu. Właściwości różnią się jednak sposobem przechowywania ich wartości.

## <a name="kinds-of-domain-properties"></a>Rodzaje właściwości domeny
 W definicji DSL można ustawić **rodzaj** właściwości domeny, jak podano w poniższej tabeli:

|Rodzaj właściwości domeny|Opis|
|-|-|
|**Standardowa** (domyślna)|Właściwość domeny, która jest zapisywana w *magazynie i* serializowana do pliku.|
|**Obliczeniowy**|Właściwość domeny tylko do odczytu, która nie jest zapisywana w magazynie, ale jest obliczana na podstawie innych wartości.<br /><br /> Na przykład wartość `Person.Age` można obliczyć na podstawie wartości `Person.BirthDate` .<br /><br /> Musisz podać kod, który wykonuje obliczenia. Zazwyczaj oblicza się wartość z innych właściwości domeny. Można jednak również używać zasobów zewnętrznych.|
|**Magazyn niestandardowy**|Właściwość domeny, która nie jest zapisywana bezpośrednio w magazynie, ale może być zarówno get, jak i ustawiona.<br /><br /> Musisz podać metody, które pobierzą i ustawią wartość.<br /><br /> Na przykład plik `Person.FullAddress` może być przechowywany w `Person.StreetAddress` plikach , i `Person.City` `Person.PostalCode` .<br /><br /> Możesz również uzyskać dostęp do zasobów zewnętrznych, na przykład w celu uzyskania i ustawienia wartości z bazy danych.<br /><br /> Kod nie powinien ustawiać wartości w magazynie, gdy `Store.InUndoRedoOrRollback` wartość jest prawdziwa. Zobacz [Transactions and Custom Setters (Transakcje i niestandardowe zestawy ustawiające).](#setters)|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Podanie kodu obliczanej lub niestandardowej właściwości magazynu
 W przypadku ustawienia właściwości Rodzaj domeny na Wartość obliczeniowa lub Magazyn niestandardowy należy podać metody dostępu. Podczas kompilowania rozwiązania zostanie w raporcie o błędzie wyświetlany komunikat o wymaganych elementach.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Aby zdefiniować obliczoną lub niestandardową właściwość magazynu

1. W dslDefinition.dsl, wybierz właściwość domeny na diagramie lub w **Eksploratorze DSL**.

2. W **oknie Właściwości** ustaw pole **Rodzaj** na **Wartość obliczeniowa** lub **Magazyn niestandardowy.**

     Upewnij się, że ustawiono również **typ,** który ma być ustawiony.

3. Kliknij **pozycję Przekształć wszystkie** szablony na pasku narzędzi **Eksplorator rozwiązań**.

4. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Zostanie wyświetlony następujący komunikat o błędzie:*"YourClass* does not contain a definition for Get *YourProperty*."

5. Kliknij dwukrotnie komunikat o błędzie.

     Zostanie otwarty plik Dsl\GeneratedCode\DomainClasses.cs lub DomainRelationships.cs. Nad wyróżnione wywołanie metody, komentarz monituje o podanie implementacji Get *YourProperty*().

    > [!NOTE]
    > Ten plik jest generowany z dslDefinition.dsl. W przypadku edytowania tego pliku zmiany zostaną utracone przy następnym kliknięciu przycisku Przekształć **wszystkie szablony.** Zamiast tego dodaj wymaganą metodę w oddzielnym pliku.

6. Utwórz lub otwórz plik klasy w oddzielnym folderze, na przykład CustomCode \\ *YourDomainClass*.cs.

     Upewnij się, że przestrzeń nazw jest taka sama jak w wygenerowanym kodzie.

7. W pliku klasy napisz częściową implementację klasy domeny. W klasie napisz definicję brakującej metody, `Get` która przypomina następujący przykład:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. W przypadku ustawienia **opcji Kind (Rodzaj)** na **wartość Custom Storage**(Magazyn niestandardowy) należy również podać metodę `Set` . Na przykład:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Kod nie powinien ustawiać wartości w magazynie, gdy `Store.InUndoRedoOrRollback` wartość jest prawdziwa. Zobacz [Transactions and Custom Setters (Transakcje i niestandardowe zestawy ustawiające).](#setters)

9. Skompiluj i uruchom rozwiązanie.

10. Przetestuj właściwość . Upewnij się, że próbujesz **cofnąć i** **ponownie wykonać polecenie**.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transakcje i niestandardowe zestawy ustawiające
 W metodzie Set właściwości Custom Storage nie trzeba otwierać transakcji, ponieważ metoda jest zwykle wywoływana wewnątrz aktywnej transakcji.

 Jednak metoda Set może być również wywoływana, jeśli użytkownik wywoła polecenie Cofnij lub Ponownie wycofuje lub jeśli transakcja jest wycofywana. W <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> przypadku wartości true metoda Set powinna zachowywać się w następujący sposób:

- Nie należy wprowadzać zmian w magazynie, takich jak przypisywanie wartości do innych właściwości domeny. Menedżer cofania ustawi ich wartości.

- Należy jednak zaktualizować wszelkie zasoby zewnętrzne, takie jak zawartość bazy danych lub pliku, lub obiekty spoza magazynu. Dzięki temu będą one przechowywane w magazynie z wartościami.

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

 Aby uzyskać więcej informacji na temat transakcji, zobacz [Nawigowanie](../modeling/navigating-and-updating-a-model-in-program-code.md)i aktualizowanie modelu w kodzie programu .

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Właściwości właściwości domeny](../modeling/properties-of-domain-properties.md)
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
