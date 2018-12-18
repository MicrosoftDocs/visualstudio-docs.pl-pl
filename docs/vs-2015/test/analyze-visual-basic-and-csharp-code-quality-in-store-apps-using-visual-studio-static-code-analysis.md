---
title: Analizowanie kodu języka Visual Basic i C# kodu jakości w aplikacjach Store przy użyciu statycznej analizy kodu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: a3a3d753f9e2dd3b046159d191149b7af062fe16
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063216"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Analizowanie jakości kodu w języku Visual Basic i C# w aplikacjach Store przy użyciu programu Visual Studio statycznej analizy kodu

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Narzędzie do analizy kodu w programie Visual Studio Express sprawdza swój kod pod kątem zestaw wspólne wady i naruszeń dobrą praktykę programistyczną. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ narzędzie do analizy kodu szuka wzorców konkretnego kodu, które są prawidłowe, ale nadal można tworzyć problemy dla Ciebie lub innych osób używających Twojego kodu. Analiza kodu, można także znaleźć defektów w kodzie, które są trudne do odnajdywania za pomocą testowania. Podczas procesu opracowywania uruchomione narzędzie do analizy kodu w regularnych odstępach czasu może zwiększyć jakość ukończonej aplikacji.

> [!NOTE]
>  W programie Visual Studio Ultimate, Visual Studio Premium i Visual Studio Professional można użyć pełnej funkcjonalności podczas analizy kodu. Zobacz [analiza jakości aplikacji za pomocą narzędzi analizy kodu](http://msdn.microsoft.com/library/dd264897.aspx) w bibliotece MSDN.

## <a name="in-this-topic"></a>W tym temacie:
 Informacje na temat:

 [Trwa uruchamianie analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Analizowanie i rozwiązywanie ostrzeżenia analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Pomijanie ostrzeżeń analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Wyszukiwanie i filtrowanie wyników analizy kodu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Ostrzeżenia analizy kodu w języku Visual Basic i C#](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

##  <a name="BKMK_Run"></a> Trwa uruchamianie analizy kodu
 Aby uruchomić analizę kodu w rozwiązaniu programu Visual Studio:

- Na **kompilacji** menu, wybierz **Uruchom analizę kodu dla rozwiązania**.

  Do automatycznego uruchamiania analizy kodu za każdym razem, tworzysz projekt:

1. Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz **właściwości**.

2. Na stronie właściwości projektu, wybierz opcję **analizy kodu** , a następnie wybierz **Włącz analizę kodu podczas kompilacji (definiuje stałą analizy)**.

   Rozwiązania jest kompilowana i uruchomieniu analizy kodu. Wyniki są wyświetlane w oknie analizy kodu.

   ![Okno analizy kodu](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

##  <a name="BKMK_Analyze"></a> Analizowanie i rozwiązywanie ostrzeżenia analizy kodu
 Aby analizować szczególne ostrzeżenie, kliknij tytuł ostrzeżenie w oknie analizy kodu. Ostrzeżenie rozwija, aby wyświetlić szczegółowe informacje o problemie.

 ![Rozwinięte ostrzeżenie analizy kodu](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Po rozwinięciu ostrzeżenie w wierszu kodu, który spowodował ostrzeżenie jest wyróżniony w edytorze kodu programu Visual Studio.

 ![Kod, wyróżnianie tekstu analizy](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Po zrozumieniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie jest już wyświetlany w oknie analizy kodu i rozwiązanie problemu nie został zgłoszony nowe ostrzeżenia.

> [!TIP]
>  Możesz ponownie uruchomić analizę kodu w oknie analizy kodu. Kliknij przycisk **analizy** przycisk, a następnie wybierz zakres analizy. Możesz ponownie uruchomić analizy na całego rozwiązania lub wybranego projektu.

##  <a name="BKMK_Suppress"></a> Pomijanie ostrzeżeń analizy kodu
 Istnieją terminy, gdy można zdecydować, Rezygnacja z naprawiania ostrzeżenie analizy kodu. Można zdecydować, rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo wystąpienia problemu w implementacji rzeczywistych swój kod. Lub może być uważa, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Poszczególne ostrzeżenia można pominąć, tak aby nie były widoczne w oknie analizy kodu.

 Aby pominąć Ostrzeżenie:

1. Jeśli nie są wyświetlane szczegółowe informacje, kliknij tytuł ostrzeżenie, aby ją rozwinąć.

2. Wybierz **akcje** widocznego u dołu ostrzeżenia.

3. Wskaż **Pomiń komunikat** , a następnie wybierz opcję **w źródłowej** lub **w pliku pominięć**.

   - **W źródle** wstawia `SuppressMessage` atrybutu w pliku źródłowym powyżej metody, która wygenerowała ostrzeżenie. To sprawia, że pomijanie mogą szybciej odnajdywać.

   - **W pliku pominięć** dodaje `SuppressMessage` atrybutu **GlobalSuppressions.cs** pliku projektu. To może ułatwić zarządzanie pominięcia. Należy pamiętać, że `SuppressMessage` dodany atrybut **GlobalSuppression.cs** wspiera także metodę, która wygenerowała ostrzeżenie. Pomijaj ostrzeżenia globalnie.

     Decyzji, czy ostrzeżenia w pliku źródłowym lub w pliku pominięć zależy od potrzeb i stylu kodowania.

##  <a name="BKMK_Search"></a> Wyszukiwanie i filtrowanie wyników analizy kodu
 Możesz wyszukiwać długim spisem komunikaty ostrzegawcze i filtrować ostrzeżeń w rozwiązaniach dotyczących wielu projektów.

 ![Wyszukiwanie i filtrowanie oknie analizy kodu](../test/media/ca-searchfilter.png "CA_SearchFilter")

 W [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)], wszystkie code analysis ostrzeżenia mają poziom ważności ostrzeżenie.

##  <a name="BKMK_Warnings"></a> Ostrzeżenia analizy kodu w języku Visual Basic i C#
 Analiza kodu generuje następujące ostrzeżenia:

 [CA1001: Typy z polami możliwymi do likwidacji powinny być możliwe do likwidacji](http://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Usuwaj puste finalizatory](http://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](http://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Zaimplementuj konstruktory serializacji](http://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](http://msdn.microsoft.com/library/ms182359.aspx)
