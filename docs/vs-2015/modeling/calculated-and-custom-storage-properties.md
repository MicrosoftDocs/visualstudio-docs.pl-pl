---
title: Obliczone i niestandardowe właściwości przechowywania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5aa6edaaba54f9c08921a594b90ca1a7352e4da
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433435"
---
# <a name="calculated-and-custom-storage-properties"></a>Obliczone i niestandardowe właściwości przechowywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wszystkie właściwości domeny w języku specyficznym dla domeny (DSL) mogą być wyświetlane użytkownikowi na diagramie, a w Eksploratorze języka i są dostępne dla kodu programu. Jednak właściwości różnią się w taki sposób, że ich wartości są przechowywane.  
  
## <a name="kinds-of-domain-properties"></a>Rodzaje właściwości domeny  
 W definicji DSL można ustawić **rodzaj** własności domeny, zgodnie z opisem w poniższej tabeli:  
  
|Rodzaj właściwości domeny|Opis|  
|--------------------------|-----------------|  
|**Standardowa** (opcja domyślna)|Właściwość domeny, który został zapisany w *przechowywania* i serializacji do pliku.|  
|**Obliczany**|Właściwość domeny tylko do odczytu, które nie są zapisywane w magazynie, ale jest obliczana na podstawie innych wartości.<br /><br /> Na przykład `Person.Age` można obliczonym na podstawie `Person.BirthDate`.<br /><br /> Należy podać kod, który wykonuje obliczenia. Zazwyczaj należy obliczyć wartość na podstawie innych właściwości domeny. Jednak można również użyć zasobów zewnętrznych.|  
|**Magazynu niestandardowego**|Właściwość domeny, które nie są zapisywane bezpośrednio w magazynie, ale może być zarówno get i set.<br /><br /> Należy podać metody get i set wartość.<br /><br /> Na przykład `Person.FullAddress` mogą być przechowywane w `Person.StreetAddress`, `Person.City`, i `Person.PostalCode`.<br /><br /> Można również dostęp do zasobów zewnętrznych, na przykład aby pobieranie i ustawianie wartości z bazy danych.<br /><br /> Twój kod nie może ustawić wartości w magazynie podczas `Store.InUndoRedoOrRollback` ma wartość true. Zobacz [transakcji i niestandardowych metod ustawiających](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Dostarczanie kodu dla właściwości magazynu obliczeniowe lub niestandardowe  
 Jeśli ustawisz rodzaj właściwości domeny obliczeniowe lub magazyn niestandardowy, należy podać metody dostępu. Podczas kompilowania rozwiązania raportu o błędach będą Powiedz, co jest wymagane.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Aby zdefiniować obliczeniowe lub właściwość magazynu niestandardowego  
  
1. W DslDefinition.dsl, wybierz właściwość domeny na diagramie lub w **Eksplorator DSL**.  
  
2. W **właściwości** oknie **rodzaj** pole **obliczona** lub **magazynu niestandardowego**.  
  
     Upewnij się, czy też ustawienie jego **typu** odpowiednią.  
  
3. Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi **Eksploratora rozwiązań**.  
  
4. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Zostanie zgłoszony następujący komunikat o błędzie: "*YourClass* nie zawiera definicji Get*YourProperty*."  
  
5. Kliknij dwukrotnie komunikat o błędzie.  
  
     Zostanie otwarty Dsl\GeneratedCode\DomainClasses.CS lub DomainRelationships.cs. Powyżej wywołanie metody wyróżnione komentarz wyświetli monit o podanie implementację Get*YourProperty*().  
  
    > [!NOTE]
    > Ten plik jest generowany na podstawie DslDefinition.dsl. Jeśli możesz edytować ten plik, zmiany zostaną utracone przy następnym kliknięciu **Przekształć wszystkie szablony**. Zamiast tego dodać wymaganej metody w oddzielnym pliku.  
  
6. Utwórz lub Otwórz plik klasy w oddzielnym folderze, na przykład atrybut CustomCode\\*YourDomainClass*. cs.  
  
     Upewnij się, że przestrzeń nazw jest taki sam jak w wygenerowanym kodzie.  
  
7. W pliku klasy Napisz częściową implementację klasy domeny. W tej klasy, napisz definicji w celu znalezienia brakujących `Get` metodę, która przypomina poniższy przykład:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8. Jeśli ustawisz **rodzaj** do **magazynu niestandardowego**, również będzie musiał podać `Set` metody. Na przykład:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Twój kod nie może ustawić wartości w magazynie podczas `Store.InUndoRedoOrRollback` ma wartość true. Zobacz [transakcji i niestandardowych metod ustawiających](#setters).  
  
9. Skompiluj i uruchom rozwiązanie.  
  
10. Testowanie właściwości. Upewnij się, że próbujesz **Cofnij** i **wykonaj ponownie**.  
  
## <a name="setters"></a> Transakcje i niestandardowych metod ustawiających.  
 W metodzie zestaw właściwości niestandardowych magazynowania nie masz do otwarcia transakcji, ponieważ metoda jest zazwyczaj wywoływana w aktywnej transakcji.  
  
 Jednak metody Set może być również wywoływane, jeśli użytkownik wywoła cofania i ponawiania lub jeśli transakcja jest wycofywana. Gdy <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> ma wartość true, metoda zestaw powinny zachowywać się w następujący sposób:  
  
- Nie należy wprowadzać zmian w magazynie, takich jak przypisywanie wartości do innych właściwości domeny. Menedżera cofania ustawi ich wartości.  
  
- Jednakże zaktualizuj dowolnych zasobów zewnętrznych, takich jak bazy danych lub zawartości pliku lub obiektów poza magazynu. Będzie to upewnij się, że są one przechowywane w synchronism z wartościami w magazynie.  
  
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
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Właściwości właściwości domeny](../modeling/properties-of-domain-properties.md)   
 [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
