---
title: Fragmenty kodu w języku Visual C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fb84854bd871277f680a753b28c17e3429283928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646718"
---
# <a name="visual-c-code-snippets"></a>Wstawki kodu Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kodu są gotowymi fragmentami kodu, które można szybko wstawić do kodu. Na przykład `for` fragment kodu tworzy pustą `for` pętlę. Niektóre fragmenty kodu są otoczone fragmentami kodu, które umożliwiają wybranie wierszy kodu, a następnie wybranie fragmentu kodu, który zawiera zaznaczone wiersze kodu. Na przykład po wybraniu wierszy kodu, a następnie aktywowaniu `for` fragmentu kodu, tworzy `for` pętlę z tymi wierszami kodu w bloku pętli. Fragmenty kodu mogą szybciej i bardziej niezawodnie pisać kod programu.

 Można wstawić fragment kodu w lokalizacji kursora lub wstawić fragment kodu otaczającego wokół aktualnie zaznaczonego kodu. Wstawianie fragmentu kodu jest wywoływane przez **Wstawianie fragmentu kodu** lub **Otocz za** pomocą poleceń w menu **IntelliSense** lub za pomocą skrótów klawiaturowych CTRL + K, a następnie X lub CTRL + K, a następnie odpowiednio.

 Wstawienie wstawka kodu zawiera nazwę fragmentu kodu dla wszystkich dostępnych fragmentów kodu. Wstawianie fragmentów kodu zawiera również okno dialogowe dane wejściowe, w którym można wpisać nazwę fragmentu kodu lub część nazwy fragmentu kodu. Wstawianie fragmentu kodu wyróżnia najbliższe dopasowanie do nazwy fragmentu kodu. Naciśnięcie klawisza TAB w dowolnym momencie spowoduje odrzucenie wstawionego fragmentu kodu i wstawienie aktualnie zaznaczonego fragmentu kodu. Wpisanie klawisza ESC lub kliknięcie myszy w edytorze kodu spowoduje odrzucenie wstawionego fragmentu kodu bez wstawiania fragmentu kodu.

## <a name="default-code-snippets"></a>Domyślne fragmenty kodu
 Domyślnie następujące fragmenty kodu są zawarte w programie Visual Studio.

|Nazwa (lub skrót)|Opis|Prawidłowe lokalizacje do wstawienia fragmentu kodu|
|--------------------------|-----------------|---------------------------------------|
|#if|Tworzy dyrektywę [#if](https://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) i [#endif](https://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) dyrektywą.|Dowolnym miejscu.|
|#region|Tworzy dyrektywę [#region](https://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) i [#endregion](https://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) dyrektywą.|Dowolnym miejscu.|
|~|Tworzy destruktor dla klasy zawierającej.|Wewnątrz klasy.|
|— atrybut|Tworzy deklarację dla klasy, która pochodzi od <xref:System.Attribute> .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|checked|Tworzy [zaznaczony](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) blok.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|class|Tworzy deklarację klasy.|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|obiektów|Tworzy Konstruktor dla klasy zawierającej.|Wewnątrz klasy.|
|CW|Tworzy wywołanie <xref:System.Console.WriteLine%2A> .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|do|Tworzy [do](https://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` pętlę do.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|else|Tworzy blok [else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|enum|Tworzy deklarację [wyliczenia](https://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|equals|Tworzy deklarację metody, która zastępuje <xref:System.Object.Equals%2A> metodę zdefiniowaną w <xref:System.Object> klasie.|Wewnątrz klasy lub struktury.|
|Oprócz|Tworzy deklarację dla klasy, która pochodzi od wyjątku (domyślnie <xref:System.Exception> ).|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|dla|Tworzy pętlę [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|foreach|Tworzy pętlę [foreach](https://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|dla|Tworzy pętlę [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) , która zmniejsza zmienną pętli po każdej iteracji.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|if|Tworzy blok [if](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|indeksatora|Tworzy deklarację indeksatora.|Wewnątrz klasy lub struktury.|
|interface|Tworzy deklarację [interfejsu](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|wywołuje|Tworzy blok, który bezpiecznie wywołuje zdarzenie.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|iterator|Tworzy iterator.|Wewnątrz klasy lub struktury.|
|iterindex|Tworzy parę iteratorów i indeksatora "Named" przy użyciu klasy zagnieżdżonej.|Wewnątrz klasy lub struktury.|
|lock|Tworzy blok [blokady](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|mbox|Tworzy wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> . Może być konieczne dodanie odwołania do System.Windows.Forms.dll.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|namespace|Tworzy deklarację [przestrzeni nazw](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) .|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|
|wierszy|Tworzy [automatycznie implementowaną](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) deklarację właściwości.|Wewnątrz klasy lub struktury.|
|propfull|Tworzy deklarację właściwości przy użyciu metod dostępu get i Set.|Wewnątrz klasy lub struktury.|
|propg|Tworzy [automatycznie zaimplementowaną Właściwość](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) tylko do odczytu z prywatnym akcesorem "Set".|Wewnątrz klasy lub struktury.|
|kartę|Tworzy [statyczną](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)deklarację metody[całkowitej int](https://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) .|Wewnątrz klasy lub struktury.|
|struktura|Tworzy deklarację [struktury](https://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) .|Wewnątrz przestrzeni nazw (łącznie z globalną przestrzenią nazw), klasą lub strukturą.|
|svm|Tworzy [statyczną](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)deklarację metody "[void](https://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) Main".|Wewnątrz klasy lub struktury.|
|switch|Tworzy blok [przełącznika](https://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|try|Tworzy blok [try-catch](https://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|tryf|Tworzy blok [try-finally](https://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|unchecked|Tworzy [niesprawdzony](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) blok.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|unsafe|Tworzy [niebezpieczny](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) blok.|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|
|using|Tworzy dyrektywę [using](https://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) .|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|
|while|Tworzy pętlę [while](https://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) .|Wewnątrz metody, indeksatora, metody dostępu do właściwości lub metodzie dostępu do zdarzeń.|

## <a name="see-also"></a>Zobacz też
 Fragmenty kodu [funkcje](../ide/code-snippet-functions.md) [fragmentów kodu](../ide/code-snippets.md) [, jak: Tworzenie nowego wstawka z](https://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338) [parametrami szablonu](../ide/template-parameters.md) zamienników [instrukcje: używanie fragmentów kodu otaczającego i](../ide/how-to-use-surround-with-code-snippets.md) [, jak: Przywracanie wstawek refaktoryzacji języka C#](../ide/how-to-restore-csharp-refactoring-snippets.md)
