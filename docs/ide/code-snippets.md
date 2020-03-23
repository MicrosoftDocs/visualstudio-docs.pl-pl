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
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585421"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu to małe bloki kodu wielokrotnego użycia, które można wstawić do pliku kodu za pomocą polecenia menu menu (menu kontekstowego) lub kombinacji skrótów klawiszowych. Zazwyczaj zawierają one często używane bloki `try-finally` `if-else` kodu, takie jak lub bloki, ale mogą być używane do wstawiania całych klas lub metod.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W programie Visual Studio dla komputerów Mac zobacz [Fragmenty kodu (Visual Studio dla komputerów Mac).](/visualstudio/mac/snippets)

Fragmenty kodu są dostępne dla wielu języków, w tym C#, C++, Visual Basic, XML i T-SQL, aby wymienić tylko kilka. Aby wyświetlić wszystkie dostępne zainstalowane fragmenty kodu języka, otwórz **Menedżera urywków kodu** z menu **Narzędzia** (lub naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**B**) i wybierz język z menu rozwijanego u góry.

![Okno dialogowe Menedżer urywków kodu](media/code-snippets-manager.png)

Dostęp do fragmentów kodu można uzyskać w następujący sposób:

- Na pasku menu wybierz pozycję **Edytuj** > **urywek wstawiania** **intellisense** > 

- Z menu kontekstowego lub kontekstowego w edytorze kodu wybierz polecenie > **Urywek wstawiania fragmentu kodu** **Snippet**

- Z klawiatury naciśnij **klawisze Ctrl**+**K**,**Ctrl**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty rozszerzania i fragmenty dźwięku przestrzennego

W programie Visual Studio istnieją dwa rodzaje fragmentu kodu: fragmenty kodu, które są dodawane w określonym punkcie wstawiania i mogą zastąpić skrót urywka i otoczyć fragmentami kodu (tylko C# i C++), które są dodawane wokół wybranego bloku kodu.

Przykład fragmentu rozszerzenia: w języku C# skrót tryf jest używany do wstawiania bloku try-finally:

```csharp
try
{

}
finally
{

}
```

Ten fragment kodu można wstawić, klikając polecenie **Wstaw fragment** kodu w menu (menu kontekstowym) okna kodu, `tryf`a następnie w programie Visual **C#,** a następnie wpisz klawisz Tab , a następnie naciśnij klawisz **Tab**. Możesz też wpisać `tryf` i **nacisnąć klawisz Tab** dwa razy.

Przykład fragmentu kodu surround z: w języku C++ skrót `if` może być używany jako fragment wstawiania lub jako fragment kodu surround. Jeśli wybierzesz wiersz kodu `return FALSE;`(na przykład ), a następnie wybierz polecenie **Surround With** > **if,** fragment kodu zostanie rozwinięty wokół linii:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry zastępowania fragmentu kodu

Urywki mogą zawierać parametry zastępcze, które są symbolami zastępczymi, które należy zastąpić, aby dopasować dokładny kod, który piszesz. W poprzednim `true` przykładzie jest parametrem zastępczym, który można zastąpić odpowiednim warunkiem. Zamiennik zostanie powtórzony dla każdego wystąpienia tego samego parametru zastępczego we wemieciach.

Na przykład w języku Visual Basic istnieje fragment kodu, który wstawia właściwość. Aby wstawić fragment kodu, wybierz polecenie**Fragment kodu urywka** **Snippet** > z menu prawym przyciskiem myszy lub kontekstowego w pliku kodu języka Visual Basic. Następnie wybierz polecenie Właściwości **wzorców** > **kodu, procedury, zdarzenia** > **Zdefiniuj właściwość**.

![Menu fragmentu kodu dla zdefiniuj właściwość](media/code-snippets-vb-property.png)

Wstawiany jest następujący kod:

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

Jeśli `newPropertyValue` zmienisz `m_property`na , `newPropertyValue` każde wystąpienie zostanie zmienione. Jeśli `String` zmienisz `Int` na w deklaracji właściwości, wartość w metodzie `Int`zestawu jest również zmieniana na .

## <a name="see-also"></a>Zobacz też

- [Instruktaż: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Jak: Rozpowszechnianie fragmentów kodu](../ide/how-to-distribute-code-snippets.md)
- [Najważniejsze wskazówki dotyczące używania fragmentów kodu](../ide/best-practices-for-using-code-snippets.md)
- [Rozwiązywanie problemów z urywkami](../ide/troubleshooting-snippets.md)
- [Fragmenty kodu języka C#](../ide/visual-csharp-code-snippets.md)
- [Fragmenty kodu języka C++](../ide/visual-cpp-code-snippets.md)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)
- [Fragmenty kodu (Visual Studio dla komputerów Mac)](/visualstudio/mac/snippets)
