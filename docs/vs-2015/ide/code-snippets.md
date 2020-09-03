---
title: Fragmenty kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b41b6e4d4a7635b32edb5697c89ecb1249fb9da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619726"
---
# <a name="code-snippets"></a>Wstawki kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kodu to małe bloki kodu wielokrotnego użytku, które można wstawić do pliku kodu przy użyciu polecenia menu kontekstowego lub kombinacji klawiszy skrótu. Zwykle zawierają one często używane bloki kodu, takie jak try-finally czy Block-else, ale mogą służyć do wstawiania całych klas lub metod.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty kodu rozwinięcia i otocz za pomocą fragmentów kodu
 W programie Visual Studio istnieją dwa rodzaje fragmentów kodu: fragmenty rozszerzające, które są dodawane w określonym punkcie wstawiania i mogą zastąpić skrót fragmentu i fragmenty kodu (tylko w języku C# i C++), które są dodawane wokół wybranego bloku.

 Przykład fragmentu kodu wstawiania: w języku C# skrót tryf jest używany do wstawiania bloku try-finally:

```
try
{

}
finally
{

}

```

 Możesz wstawić ten fragment kodu, klikając **Wstaw fragment kodu** w menu kontekstowym okna kod, a następnie **Visual C#**, następnie wpisz `tryf` , a następnie Tab, lub wpisując `tryf` i naciskając klawisz Tab + Tab.

 Przykład fragmentu kodu otaczającego: w języku C++ `if` można użyć skrótu jako fragmentu kodu wstawiania lub jako fragmentu kodu. Jeśli zaznaczysz wiersz kodu (na przykład `return FALSE;` ), a następnie klikniesz opcję **Otocz z**, a następnie, **Jeśli**, fragment jest rozwinięty wokół wiersza:

```
if (true)
{
    return FALSE;
}

```

## <a name="snippet-replacement-parameters"></a>Parametry zamiany fragmentu kodu
 Fragmenty kodu mogą zawierać parametry zastępcze, które są symbolami zastępczymi, które należy zastąpić, aby dopasować do precyzyjnego kodu, który piszesz. W poprzednim przykładzie `true` jest parametrem zastępczym, który powinien zostać zamieniony na odpowiedni warunek. Zastępowana zmiana jest powtarzana dla każdego wystąpienia tego samego parametru zastępującego w fragmencie kodu.

 Na przykład, w Visual Basic istnieje fragment kodu, który wstawia właściwość. Kliknij przycisk **Wstaw fragment** kodu z menu kontekstowego okna kod, następnie **wzorce kodów**, następnie **właściwości, procedury, zdarzenia**, a następnie zdefiniuj właściwość. Zostanie wstawiony następujący kod:

```
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

## <a name="code-snippet-manager"></a>Menedżer fragmentów kodu
 Można wyświetlić wszystkie fragmenty kodu, które są obecnie zainstalowane, oraz ich lokalizację na dysku, klikając kolejno pozycje **Narzędzia/fragmenty kodu**. Fragmenty kodu są wyświetlane w języku.

 Katalogi wstawek można dodawać i usuwać za pomocą przycisków **Dodaj** i **Usuń** w oknie dialogowym **Menedżer fragmentów kodu** . Aby dodać poszczególne fragmenty kodu, użyj przycisku **Importuj** .

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md) , [jak: rozkładanie fragmentów kodu](../ide/how-to-distribute-code-snippets.md) [w celu użycia fragmentów kodu](../ide/best-practices-for-using-code-snippets.md) [Rozwiązywanie problemów z](../ide/troubleshooting-snippets.md) fragmentami [kodu Visual C#](../ide/visual-csharp-code-snippets.md) [Visual C++](../ide/visual-cpp-code-snippets.md) fragmenty kodu fragmenty kodu odwołania do [schematu](../ide/code-snippets-schema-reference.md)
