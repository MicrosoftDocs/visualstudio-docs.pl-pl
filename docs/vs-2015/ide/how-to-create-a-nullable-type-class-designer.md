---
title: 'Instrukcje: Tworzenie typu Zerowalnego (Projektant klas) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c71c0e7f8961b5f7c545fb59597cdd173230fc08
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680505"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Instrukcje: Tworzenie typu Zerowalnego (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre typy wartości nie zawsze masz (lub potrzebujesz) zdefiniowanej wartości. Jest to powszechną praktyką w bazach danych, gdzie niektóre pola nie można przypisać dowolną wartość. Na przykład może przypisać wartości null z polem bazy danych, aby oznaczają, że nie jeszcze nadano jej wartość.  
  
 A *typu dopuszczającego wartość null* jest typem wartości, które można rozszerzyć, aby przyspieszyć typowy zakres wartości dla tego typu, a także wartość null. Na przykład dopuszczający wartości null z `Int32`, są również oznaczane jako dopuszczającego wartość null\<Int32 > można przypisać dowolną wartość od -2147483648 do 2147483647 i może ona zostać przypisana wartość null. Nullable\<bool > można przypisać wartości `True`, `False`, lub wartość null (Brak wartości wszystkie).  
  
 Typy dopuszczające wartości null są wystąpieniami <xref:System.Nullable%601> struktury. Każde wystąpienie typu dopuszczającego wartość null, ma dwa publiczne właściwości tylko do odczytu, `HasValue` i `Value`:  
  
- `HasValue` Typ jest `bool` i wskazuje, czy zmienna zawiera wartość zdefiniowana. `True` oznacza, że zmienna zawiera wartość inną niż null. Możesz sprawdzić wartości zdefiniowanej przy użyciu instrukcji takich jak `if (x.HasValue)` lub `if (y != null)`.  
  
- `Value` jest taki sam typ co typ podstawowy. Jeśli `HasValue` jest `True`, `Value` zawiera odpowiednią wartość. Jeśli `HasValue` jest `False`, uzyskiwania dostępu do `Value` spowoduje zgłoszenie wyjątku dotyczącego nieprawidłowej operacji.  
  
  Domyślnie, kiedy Deklarujesz zmienną typu dopuszczającego wartość null, go nie ma zdefiniowanej wartości (`HasValue` jest `False`), inne niż domyślna wartość typu wartości podstawowej.  
  
  Projektant klas Wyświetla typ dopuszczający wartość null, tak samo, jak wyświetla jego typ podstawowy.  
  
  Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku Visual C#, zobacz [typów dopuszczających wartości zerowe](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku Visual Basic, zobacz [typów wartości dopuszczających wartości zerowe](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Aby dodać typ dopuszczający wartość null, za pomocą projektanta klas  
  
1. Na diagramie klasy należy rozwinąć istniejącej klasy, lub Utwórz nową klasę.  
  
2. Aby dodać klasę do projektu, na **Diagram klas** menu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3. Aby rozwinąć kształt klasy na **Diagram klas** menu, kliknij przycisk **rozwiń**.  
  
4. Wybierz kształt klasy. Na **Diagram klas** menu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **pola**. Nowe pole o nazwie domyślnej **pola** pojawi się w kształt klasy, a także w **szczegóły klasy** okna.  
  
5. W **nazwa** kolumny **szczegóły klasy** okna (lub w klasie kształtu, sam), Zmień nazwę nowego pola do nazwy ważne i istotne.  
  
6. W **typu** kolumny **szczegóły klasy** oknie zadeklarowana jako typ dopuszczający wartość null, jak pokazano w poniższym kodzie:  
  
    ```csharp  
    // Declare a nullable type in Visual C#:  
    class Test  
    {  
       int? building_number = 5;  
    }  
    ```  
  
    ```vb  
    ' Declare a nullable type in Visual Basic:  
    Class Test  
       Dim buildingNumber As Nullable(Of Integer) = 5  
    End Class  
    ```  
  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Aby dodać typ dopuszczający wartość null, za pomocą edytora kodu  
  
1. Dodaj klasę do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **Dodaj klasę**.  
  
2. W pliku CS lub .vb dla nowej klasy należy dodać co najmniej jeden typ dopuszczający wartość null w nowej klasie do deklaracji klasy.  
  
3. W widoku klas przeciągnij nową ikonę klasy do powierzchni projektowej projektanta klas. Kształt klasy pojawia się na diagramie klasy.  
  
4. Rozwiń szczegóły kształt klasy, a następnie przesuń wskaźnik myszy nad składowych klasy. Etykietka narzędzia zawiera deklarację każdego elementu członkowskiego.  
  
5. Kliknij prawym przyciskiem myszy kształt klasy, a następnie kliknij przycisk **szczegóły klasy**. Można wyświetlać lub modyfikować właściwości nowego typu w **szczegóły klasy** okna.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Nullable%601>   
 [Typy dopuszczające wartości zerowe](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6)   
 [Przy użyciu typów dopuszczających wartości zerowe](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)   
 [Instrukcje: Identyfikowanie typu dopuszczającego wartość null](https://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387)   
 [Typy wartości dopuszczających wartości null](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)
