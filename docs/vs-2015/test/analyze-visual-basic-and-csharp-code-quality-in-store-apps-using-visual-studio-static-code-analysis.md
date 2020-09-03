---
title: Analizowanie jakości kodu Visual Basic i C# w aplikacjach ze sklepu przy użyciu statycznej analizy kodu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cfe5ed57bfc361b711ed2aceceff2aabfc44cf4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660739"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Analizowanie jakości kodu Visual Basic i C# w aplikacjach ze sklepu przy użyciu statycznej analizy kodu programu Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Narzędzie do analizy kodu w Visual Studio Express bada kod dla zestawu typowych wad i naruszeń dobrych rozwiązań programistycznych. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń kompilatora, ponieważ Narzędzie analizy kodu wyszukuje określone wzorce kodu, które są prawidłowe, ale mogą nadal tworzyć problemy dla Ciebie lub innych osób korzystających z Twojego kodu. Analiza kodu może również znaleźć wady w kodzie, które trudno wykryć poprzez testowanie. Uruchamianie narzędzia do analizy kodu w regularnych odstępach czasu w procesie tworzenia oprogramowania może zwiększyć jakość ukończonej aplikacji.

> [!NOTE]
> W Visual Studio Ultimate, Visual Studio Premium i Visual Studio Professional można użyć pełnej funkcjonalności analizy kodu. Zobacz [Analizowanie jakości aplikacji za pomocą narzędzi do analizy kodu](https://msdn.microsoft.com/library/dd264897.aspx) w bibliotece MSDN.

## <a name="in-this-topic"></a>W tym temacie:
 Możesz uzyskać informacje na temat:

 [Uruchamianie analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Pomijanie ostrzeżeń analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Wyszukiwanie i filtrowanie wyników analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Ostrzeżenia analizy kodu Visual Basic i C#](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

## <a name="running-code-analysis"></a><a name="BKMK_Run"></a> Uruchamianie analizy kodu
 Aby uruchomić analizę kodu w rozwiązaniu programu Visual Studio:

- W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w rozwiązaniu**.

  Aby automatycznie uruchomić analizę kodu przy każdej kompilacji projektu:

1. Kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań a następnie wybierz polecenie **Właściwości**.

2. Na stronie właściwości projektu wybierz pozycję **Analiza kodu** , a następnie wybierz pozycję **Włącz analizę kodu podczas kompilacji (definiuje stałą CodeAnalysis)**.

   Rozwiązanie jest kompilowane i zostanie uruchomiona Analiza kodu. Wyniki pojawiają się w oknie Analiza kodu.

   ![Okno analizy kodu](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

## <a name="analyzing-and-resolving-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu
 Aby przeanalizować określone ostrzeżenie, kliknij tytuł ostrzeżenia w oknie Analiza kodu. Ostrzeżenie zostanie rozwinięte, aby wyświetlić szczegółowe informacje o problemie.

 ![Ostrzeżenie o rozszerzonej analizie kodu](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Po rozszerzeniu ostrzeżenia wiersz kodu, który spowodował ostrzeżenie, jest wyróżniony w edytorze kodu programu Visual Studio.

 ![Podświetlanie tekstu analizy kodu](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Po zrozumieniu problemu można go rozwiązać w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie pojawia się już w oknie Analiza kodu i że poprawka nie wywołała nowych ostrzeżeń.

> [!TIP]
> Możesz ponownie uruchomić analizę kodu z okna Analiza kodu. Kliknij przycisk **Analizuj** i wybierz zakres analizy. Możesz ponownie uruchomić analizę całego rozwiązania lub w wybranym projekcie.

## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Pomijanie ostrzeżeń analizy kodu
 Istnieją przypadki, w których można zrezygnować z naprawienia ostrzeżenia analizy kodu. Użytkownik może zdecydować, że rozwiązanie tego problemu wymaga zbyt dużo ponownego kodowania w odniesieniu do prawdopodobieństwa, że problem będzie występował w jakiejkolwiek rzeczywistej implementacji kodu. Można też zastanowić się, że analiza, która jest używana w ostrzeżeniu, jest nieodpowiedni dla danego kontekstu. Możesz pominąć poszczególne ostrzeżenia, aby nie były wyświetlane w oknie Analiza kodu.

 Aby pominąć ostrzeżenie:

1. Jeśli szczegółowe informacje nie są wyświetlane, kliknij tytuł ostrzeżenia, aby go rozwinąć.

2. Wybierz łącze **Akcje** u dołu ostrzeżenia.

3. Wskaż pozycję **Pomiń komunikat** , a następnie wybierz pozycję **w polu Źródło** lub **w pliku**pominięć.

   - **W obszarze Źródło** wstawia `SuppressMessage` atrybut w pliku źródłowym powyżej metody, która wygenerowała ostrzeżenie. To sprawia, że pomijanie jest bardziej wykrywalne.

   - **W pliku** pominięć dodaje `SuppressMessage` atrybut do pliku **GlobalSuppressions.cs** projektu. Może to ułatwić zarządzanie pominięciami. Należy zauważyć, że `SuppressMessage` atrybut dodany do **GlobalSuppression.cs** również odwołuje się do metody, która wygenerowała ostrzeżenie. Nie powoduje pomijania ostrzeżenia globalnie.

     Decyzja o tym, czy pomijać ostrzeżenie w pliku źródłowym lub w pliku pominięć, zależy od stylu kodowania i potrzeb.

## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Wyszukiwanie i filtrowanie wyników analizy kodu
 Można wyszukiwać długie listy komunikatów ostrzegawczych i filtrować ostrzeżenia w rozwiązaniach w ramach projektu.

 ![Wyszukiwanie i filtrowanie okna Analiza kodu](../test/media/ca-searchfilter.png "CA_SearchFilter")

 W programie [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)] wszystkie ostrzeżenia analizy kodu mają poziom ważności ostrzeżenie.

## <a name="visual-basic-and-c-code-analysis-warnings"></a><a name="BKMK_Warnings"></a> Ostrzeżenia analizy kodu Visual Basic i C#
 Analiza kodu wywołuje następujące ostrzeżenia:

 [CA1001: Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji](https://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Usuwaj puste finalizatory](https://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: Pola możliwe do likwidacji należy likwidować](https://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Zaimplementuj konstruktory serializacji](https://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](https://msdn.microsoft.com/library/ms182359.aspx)
