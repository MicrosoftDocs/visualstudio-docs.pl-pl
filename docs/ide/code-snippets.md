---
title: Fragmenty kodu
description: Dowiedz się więcej na temat fragmentów kodu i ich małych bloków kodu wielokrotnego użytku, które można wstawić do pliku kodu.
ms.custom: SEO-VS-2020
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
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 642bfe9fdccaa607476facb792120502437cb4b8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841972"
---
# <a name="code-snippets"></a>Fragmenty kodu

Fragmenty kodu to małe bloki kodu wielokrotnego użytku, które można wstawić do pliku kodu przy użyciu menu rozwijanego prawym przyciskiem myszy (menu kontekstowe) lub kombinacji klawiszy skrótu. Zwykle zawierają one często używane bloki kodu, takie jak `try-finally` lub `if-else` bloki, ale mogą służyć do wstawiania całych klas lub metod.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [fragmenty kodu (Visual Studio dla komputerów Mac)](/visualstudio/mac/snippets).

Fragmenty kodu są dostępne dla wielu języków, w tym C#, C++, Visual Basic, XML i T-SQL, aby nazwać kilka. Aby wyświetlić wszystkie dostępne, zainstalowane fragmenty kodu dla danego języka, Otwórz **Menedżera wstawek kodów** z menu **Narzędzia** (lub naciśnij **klawisze CTRL** + **K**, **Ctrl** + **B**) i wybierz język z menu rozwijanego u góry.

![Okno dialogowe Menedżer fragmentów kodu](media/code-snippets-manager.png)

Można uzyskać dostęp do fragmentów kodu w następujący sposób:

- Na pasku menu wybierz polecenie **Edytuj**  >    >  **wstawka** IntelliSense.

- W edytorze kodu po kliknięciu prawym przyciskiem myszy lub w menu kontekstowym **Wybierz**  >  **Wstaw fragmenty** kodu

- Na klawiaturze naciśnij **klawisze CTRL** + **K**,**Ctrl** + **X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty kodu rozwinięcia i otocz za pomocą fragmentów kodu

W programie Visual Studio istnieją dwa rodzaje fragmentów kodu: fragmenty rozszerzające, które są dodawane w określonym punkcie wstawiania i mogą zastąpić skrót fragmentu i fragmenty kodu (tylko w języku C# i C++), które są dodawane wokół wybranego bloku.

Przykład fragmentu rozszerzenia: w języku C# skrót tryf jest używany do wstawiania bloku try-finally:

```csharp
try
{

}
finally
{

}
```

Możesz wstawić ten fragment kodu, klikając **Wstaw fragment kodu** w menu rozwijanym prawym przyciskiem myszy (menu kontekstowe) okna kod, a następnie **Visual C#**, następnie wpisz `tryf` , a następnie naciśnij klawisz **Tab**. Możesz również wpisać `tryf` i nacisnąć klawisz **Tab** dwa razy.

Przykład fragmentu kodu otaczającego: w języku C++ `if` można użyć skrótu jako fragmentu kodu wstawiania lub jako fragmentu kodu. Jeśli zaznaczysz wiersz kodu (na przykład `return FALSE;` ), a następnie wybierzesz opcję **Otocz za pomocą** elementu  >  **if**, fragment kodu jest rozwinięty wokół wiersza:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry zamiany fragmentu kodu

Fragmenty kodu mogą zawierać parametry zastępcze, które są symbolami zastępczymi, które należy zastąpić, aby dopasować do precyzyjnego kodu, który piszesz. W poprzednim przykładzie `true` jest parametrem zastępczym, który powinien zostać zamieniony na odpowiedni warunek. Zastępowana zmiana jest powtarzana dla każdego wystąpienia tego samego parametru zastępującego w fragmencie kodu.

Na przykład, w Visual Basic istnieje fragment kodu, który wstawia właściwość. Aby wstawić fragment kodu **, wybierz Wstaw**  >  **fragment** kodu z menu po kliknięciu prawym przyciskiem myszy lub w pliku z kodem Visual Basic. Następnie wybierz kolejno pozycje właściwości **wzorców kodu**  >  **, procedury, zdarzenia**  >  **definiują Właściwość**.

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

Jeśli zmienisz `newPropertyValue` się na `m_property` , każde wystąpienie programu `newPropertyValue` zostanie zmienione. Jeśli zmienisz `String` się na `Int` w deklaracji właściwości, wartość w metodzie Set również zostanie zmieniona na `Int` .

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Instrukcje: dystrybuowanie fragmentów kodu](../ide/how-to-distribute-code-snippets.md)
- [Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](../ide/best-practices-for-using-code-snippets.md)
- [Fragmenty kodu rozwiązywania problemów](../ide/troubleshooting-snippets.md)
- [Fragmenty kodu w języku C#](../ide/visual-csharp-code-snippets.md)
- [Fragmenty kodu języka C++](../ide/visual-cpp-code-snippets.md)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)
- [Fragmenty kodu (Visual Studio dla komputerów Mac)](/visualstudio/mac/snippets)
