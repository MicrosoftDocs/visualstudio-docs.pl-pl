---
title: Fragmenty kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 09f6e2e9b4b89c7e6fd1fe9a342d4fd05b12e7a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747980"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu to małe bloki kodu wielokrotnego użytku, które można wstawić do pliku kodu przy użyciu menu rozwijanego prawym przyciskiem myszy (menu kontekstowe) lub kombinacji klawiszy skrótu. Zwykle zawierają one często używane bloki kodu, takie jak `try-finally` lub `if-else` bloki, ale mogą służyć do wstawiania całych klas lub metod.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [fragmenty kodu (Visual Studio dla komputerów Mac)](/visualstudio/mac/snippets).

Fragmenty kodu są dostępne dla wielu języków, w tym C#, C++, Visual Basic, XML i T-SQL, do ich nazwy. Aby wyświetlić wszystkie dostępne, zainstalowane fragmenty kodu dla danego języka, Otwórz **Menedżera fragmentów kodów** z menu **Narzędzia** (lub naciśnij **klawisze Ctrl** +**K**, **Ctrl** +**B**) i wybierz język z menu rozwijanego. w górnej części strony.

![Okno dialogowe Menedżer fragmentów kodu](media/code-snippets-manager.png)

Można uzyskać dostęp do fragmentów kodu w następujący sposób:

- Na pasku menu wybierz polecenie **edytuj**  > **IntelliSense**  > **Wstaw fragment kodu**

- W edytorze kodu po kliknięciu prawym przyciskiem myszy lub menu kontekstowym wybierz **wstawkę  > ** **Wstaw fragment** kodu

- Na klawiaturze naciśnij klawisz **ctrl** +**K**,**Ctrl** +**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty kodu rozwinięcia i otocz za pomocą fragmentów kodu

W programie Visual Studio istnieją dwa rodzaje fragmentów kodu: fragmenty rozszerzające, które są dodawane w określonym punkcie wstawiania i mogą zastąpić skrót fragmentu oraz fragmenty kodu (C# i C++ tylko), które są dodawane wokół wybranego bloku.

Przykład fragmentu rozszerzenia: w C# tryf skrótu jest używany do wstawiania bloku try-finally:

```csharp
try
{

}
finally
{

}
```

Możesz wstawić ten fragment kodu, klikając **Wstaw fragment kodu** w menu rozwijanym prawym przyciskiem myszy (menu kontekstowe) okna kod, a następnie pozycję **C#Wizualizacja**, a następnie wpisując `tryf`, a następnie naciskając klawisz **Tab**. Możesz też wpisać `tryf` i dwukrotnie nacisnąć klawisz **Tab** .

Przykład fragmentu kodu otaczającego: w C++ `if` skrótu można użyć jako fragmentu kodu wstawiania lub jako fragmentu kodu. Jeśli zaznaczysz wiersz kodu (na przykład `return FALSE;`), a następnie wybierz opcję **Otocz z**  > ,**Jeśli**, fragment kodu jest rozwinięty wokół wiersza:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry zamiany fragmentu kodu

Fragmenty kodu mogą zawierać parametry zastępcze, które są symbolami zastępczymi, które należy zastąpić, aby dopasować do precyzyjnego kodu, który piszesz. W poprzednim przykładzie `true` jest parametrem zastępczym, który powinien zostać zamieniony na odpowiedni warunek. Zastępowana zmiana jest powtarzana dla każdego wystąpienia tego samego parametru zastępującego w fragmencie kodu.

Na przykład, w Visual Basic istnieje fragment kodu, który wstawia właściwość. Aby wstawić **fragment kodu, wybierz** wstawka  > **Wstaw fragment** kodu z menu po kliknięciu prawym przyciskiem myszy lub w pliku z kodem Visual Basic. Następnie wybierz **wzorce kodu**  > **właściwości, procedury, zdarzenia**  > **definiują Właściwość**.

![Menu fragmentu kodu do definiowania właściwości](media/code-snippets-vb-property.png)

Zostanie wstawiony następujący kod:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Jeśli zmienisz `newPropertyValue` na `m_property`, każde wystąpienie `newPropertyValue` zostanie zmienione. Jeśli zmienisz `String` na `Int` w deklaracji właściwości, wartość w metodzie Set zostanie również zmieniona na `Int`.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Instrukcje: dystrybuowanie fragmentów kodu](../ide/how-to-distribute-code-snippets.md)
- [Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](../ide/best-practices-for-using-code-snippets.md)
- [Fragmenty kodu rozwiązywania problemów](../ide/troubleshooting-snippets.md)
- [C#fragmenty kodu](../ide/visual-csharp-code-snippets.md)
- [C++fragmenty kodu](../ide/visual-cpp-code-snippets.md)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)
- [Fragmenty kodu (Visual Studio dla komputerów Mac)](/visualstudio/mac/snippets)
