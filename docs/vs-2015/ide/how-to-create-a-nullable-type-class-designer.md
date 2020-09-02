---
title: 'Instrukcje: Tworzenie typu dopuszczającego wartość null (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 438f84a172c7e0a2d0dc957c578adc568a46495f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668158"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Porady: tworzenie typu zerowalnego (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre typy wartości nie zawsze mają określoną wartość (lub potrzebują). Jest to typowa sytuacja w bazach danych, w których niektóre pola mogą nie mieć przypisanej żadnej wartości. Na przykład możesz przypisać wartość null do pola bazy danych, aby oznaczać, że nie została jeszcze przypisana wartość.

 *Typ dopuszczający wartość null* jest typem wartości, który można rozciągnąć, tak aby miał typowy zakres wartości dla tego typu, a także wartość null. Na przykład wartość null, która jest `Int32` również oznaczona jako Nullable \<Int32> , może być przypisana do wartości od-2147483648 do 2147483647 lub może być przypisana wartość null. Do wartości dopuszczającej wartość null \<bool> można przypisać wartość `True` , `False` lub wartość null (bez żadnej wartości).

 Typy dopuszczające wartości null są wystąpieniami <xref:System.Nullable%601> struktury. Każde wystąpienie typu dopuszczającego wartość null ma dwie publiczne właściwości tylko do odczytu `HasValue` i `Value` :

- `HasValue` jest typu `bool` i wskazuje, czy zmienna zawiera zdefiniowaną wartość. `True` oznacza, że zmienna zawiera wartość różną od null. Można testować pod kątem zdefiniowanej wartości przy użyciu instrukcji, takiej jak `if (x.HasValue)` lub `if (y != null)` .

- `Value` jest tego samego typu co typ podstawowy. Jeśli `HasValue` jest `True` , `Value` zawiera zrozumiałą wartość. Jeśli `HasValue` jest `False` , uzyskanie dostępu `Value` spowoduje zgłoszenie nieprawidłowego wyjątku operacji.

  Domyślnie podczas deklarowania zmiennej jako typu dopuszczającego wartość null nie ma zdefiniowanej wartości ( `HasValue` is `False` ), innej niż domyślna wartość jego bazowego typu wartości.

  Projektant klas wyświetla typ dopuszczający wartość null, tak jak wyświetla jego typ podstawowy.

  Aby uzyskać więcej informacji na temat typów dopuszczających wartości null w Visual C#, zobacz [Typy dopuszczające wartości null](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Aby uzyskać więcej informacji na temat typów dopuszczających wartości null w Visual Basic, zobacz [dopuszczanie typów wartości null](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Aby dodać typ dopuszczający wartość null przy użyciu Projektant klas

1. Na diagramie klasy rozwiń istniejącą klasę lub Utwórz nową klasę.

2. Aby dodać klasę do projektu, w menu **Diagram klas** kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

3. Aby rozwinąć kształt klasy, w menu **Diagram klas** kliknij przycisk **Rozwiń**.

4. Wybierz kształt klasy. W menu **Diagram klas** kliknij przycisk **Dodaj**, a następnie kliknij przycisk **pole**. Nowe pole, które ma **pole** nazwa domyślna, pojawi się w kształcie klasy, a także w oknie **Szczegóły klasy** .

5. W kolumnie **Nazwa** okna **Szczegóły klasy** (lub samego kształtu klasy) Zmień nazwę nowego pola na prawidłową i zrozumiałą nazwę.

6. W kolumnie **Typ** okna **Szczegóły klasy** Zadeklaruj typ jako typ dopuszczający wartość null, jak pokazano w poniższym kodzie:

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

### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Aby dodać typ dopuszczający wartość null przy użyciu edytora kodu

1. Dodaj klasę do projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Dodaj klasę**.

2. W pliku CS lub VB dla nowej klasy Dodaj jeden lub więcej typów wartości null w nowej klasie do deklaracji klasy.

3. W Widok klasy Przeciągnij nową ikonę klasy do Projektant klas powierzchni projektowej. Kształt klasy zostanie wyświetlony na diagramie klas.

4. Rozwiń szczegóły kształtu klasy i przesuń wskaźnik myszy nad składowe klasy. W etykietce narzędzia zostanie wyświetlona deklaracja każdego elementu członkowskiego.

5. Kliknij prawym przyciskiem myszy kształt klasy, a następnie kliknij pozycję **Szczegóły klasy**. Właściwości nowego typu można wyświetlić lub zmodyfikować w oknie **Szczegóły klasy** .

## <a name="see-also"></a>Zobacz też
 <xref:System.Nullable%601>[Typy dopuszczające wartości null](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6) [wykorzystujące Typy dopuszczające wartość null](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28) [w sposobie: Identyfikowanie](https://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387) [typów wartości](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6) dopuszczających wartość null
