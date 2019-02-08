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
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 98dadaed75cf16ae6ae35da9d6589355a63bd35c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908455"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu pochodzą małych blokach kodu wielokrotnego użytku, które mogą być wstawiane w pliku kodu za pomocą polecenia (menu kontekstowe) kliknij prawym przyciskiem myszy menu lub kombinacji klawiszy dostępu. Zwykle zawierają bloki kodu często używane, takich jak `try-finally` lub `if-else` bloków, ale może służyć do wstawienia całej klasy lub metody.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [(Visual Studio dla komputerów Mac) fragmenty kodu](/visualstudio/mac/snippets).

Fragmenty kodu są dostępne dla wielu języków, w tym C#, C++, Visual Basic, XML i T-SQL, kilka. Aby wyświetlić wszystkie dostępne zainstalowane fragmenty kodu w języku, otwórz **Menedżera wstawek kodu** z **narzędzia** menu w programie Visual Studio, a następnie wybierz język z listy rozwijanej w górnej.

![Okno dialogowe Menedżer fragmentów kodu](media/code-snippets-manager.png)

Fragmenty kodu jest możliwy z następujących metod ogólnych:

- Na pasku menu wybierz **Edytuj** > **IntelliSense** > **Wstaw fragment kodu**

- Wybierz z menu kontekście lub kliknij prawym przyciskiem myszy w edytorze kodu **fragment** > **Wstaw fragment kodu**

- Przy użyciu klawiatury, naciśnij klawisz **Ctrl**+**K**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty rozszerzeń i fragmentów Otocz przez

W programie Visual Studio, istnieją dwa rodzaje fragmentu kodu: fragmenty kodu rozszerzenia, które są dodawane w punkcie wstawiania określonego i mogą zastąpić skrótów fragmentu kodu, i z funkcji Otocz przez fragmentów kodu (C# i C++ tylko), które są dodawane wokół zaznaczonego bloku kodu.

Przykład fragment kodu rozwinięcia: w C# tryf skrótu służy do wstawiania blok try-finally:

```csharp
try
{

}
finally
{

}
```

Ten fragment kodu można wstawić, klikając **Wstaw fragment kodu** w menu kliknij prawym przyciskiem myszy (menu kontekstowe) w oknie kodu, następnie **Visual C#** , a następnie wpisz `tryf`, a następnie naciśnij klawisz  **Karta**. Alternatywnie możesz wpisać `tryf` i naciśnij klawisz **kartę** dwa razy.

Przykład fragmentu kodu z funkcji Otocz przez: w języku C++ skrót `if` może służyć jako fragment wstawiania lub z funkcji Otocz przez fragment kodu. Jeśli wybierzesz wiersz kodu (na przykład `return FALSE;`), a następnie wybierz **Otocz** > **Jeśli**, fragment kodu jest rozwinięty wokół linii:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry zamiany fragmentu kodu

Fragmenty mogą zawierać zastąpienia parametrów, które są symbolami zastępczymi, które należy zastąpić do pisania kodu dokładne dopasowania. W poprzednim przykładzie `true` parametr zastąpienia, należy zastąpić za pomocą odpowiedniego warunku. Wprowadzone zastąpienia jest powtarzany dla każdego wystąpienia parametru zastępowania we fragmencie kodu.

Na przykład w języku Visual Basic istnieje fragment kodu, który wstawia właściwości. Aby wstawić fragment kodu, wybierz opcję **fragment** > **Wstaw fragment kodu** kontekście lub kliknij prawym przyciskiem myszy w menu plik kodu w języku Visual Basic. Następnie wybierz **wzorców kodu** > **właściwości, procedury, zdarzenia** > **Zdefiniuj właściwość**.

![Menu fragment kodu dla Zdefiniuj właściwość](media/code-snippets-vb-property.png)

Poniższy kod dodaje się:

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

Jeśli zmienisz `newPropertyValue` do `m_property`, następnie każde wystąpienie `newPropertyValue` zostanie zmieniony. Jeśli zmienisz `String` do `Int` w deklaracji właściwości, następnie wartość w metodzie zestaw jest również zmienić `Int`.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Instrukcje: Dystrybuowanie fragmentów kodu](../ide/how-to-distribute-code-snippets.md)
- [Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](../ide/best-practices-for-using-code-snippets.md)
- [Rozwiązywanie problemów z fragmentów kodu](../ide/troubleshooting-snippets.md)
- [C#fragmenty kodu](../ide/visual-csharp-code-snippets.md)
- [Fragmenty kodu w usłudze Visual C++](../ide/visual-cpp-code-snippets.md)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)
- [Fragmenty kodu (Visual Studio dla komputerów Mac)](/visualstudio/mac/snippets)