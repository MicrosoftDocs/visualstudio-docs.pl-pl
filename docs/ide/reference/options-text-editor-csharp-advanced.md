---
title: Opcje, edytor tekstu, C#, zaawansowane
description: Dowiedz się, jak za pomocą strony Zaawansowane w sekcji języka C# zmodyfikować ustawienia formatowania edytora, refaktoryzacji kodu i komentarzy dokumentacji XML dla języka C#.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 29f6dd2b4a101132bc7bc19664c51fd5d4b8283e
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351994"
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane

Strona **Opcje zaawansowane pozwala** zmodyfikować ustawienia formatowania edytora, refaktoryzacji kodu i komentarzy dokumentacji XML dla języka C#. Aby uzyskać dostęp do tej strony opcji, wybierz **pozycję Narzędzia**  >  **Opcje**, a następnie wybierz pozycję Edytor **tekstu**  >  **C#**  >  **Zaawansowane.**

> [!NOTE]
> Nie wszystkie opcje mogą być wymienione w tym miejscu.

## <a name="analysis"></a>Analiza

- Analiza kodu na żywo lub zakres analizy w tle

   Skonfiguruj zakres analizy w tle dla kodu zarządzanego. Aby uzyskać więcej informacji, [zobacz Jak skonfigurować zakres analizy kodu na żywo dla kodu zarządzanego.](../../code-quality/configure-live-code-analysis-scope-managed-code.md)

## <a name="using-directives"></a>Using, dyrektywy

- Umieść najpierw dyrektywy "System" podczas sortowania using

   Po wybraniu polecenia Usuń i sortuj **usings** w menu dostępnym po kliknięciu prawym przyciskiem myszy sortuje dyrektywy i umieszcza przestrzenie nazw `using` "System" w górnej części listy.

   Przed sortowaniem:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po posortowaniu:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Oddzielanie przy użyciu grup dyrektyw

   Po wybraniu Usuń i sortuj using **polecenie** w menu prawym przyciskiem myszy oddziela dyrektywy wstawiając pusty wiersz między grupami dyrektyw, które mają tę samą główną przestrzeń `using` nazw.

   Przed sortowaniem:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po posortowaniu:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

::: moniker range=">=vs-2019"                                              
- Sugerowanie using dla typów w .NET Framework zestawów
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Sugerowanie using dla typów w zestawach odwoływnych
::: moniker-end                                                            

- Sugerowanie using dla typów w pakietach NuGet

   Po wybraniu tych opcji dostępna [jest](../quick-actions.md) szybka akcja instalowania pakietu NuGet i dodawania dyrektywy `using` dla nieużywanych typów.

   ![Szybka akcja instalowania pakietu NuGet w Visual Studio](media/nuget-lightbulb.png)

- Dodawanie brakujących dyrektyw using przy wklejaniu

    Po wybraniu tej opcji dyrektywy zostaną automatycznie dodane do kodu po `using` wklejeniu typu do pliku.

## <a name="highlighting"></a>Wyróżnianie

- Wyróżnianie odwołań do symbolu pod kursorem

   Gdy kursor znajduje się wewnątrz symbolu lub po kliknięciu symbolu wszystkie wystąpienia tego symbolu w pliku kodu są wyróżnione.

## <a name="outlining"></a>Tworzenie konspektu

- Wprowadzanie trybu liningu podczas otwierania plików

   Po wybraniu automatycznie tworzy konspekt pliku kodu, który tworzy zwijane bloki kodu. Przy pierwszym otwarciu pliku bloków #regions zwijanie nieaktywnych bloków kodu.

- Pokazywanie separatorów linii procedury

   Edytor tekstu wskazuje wizualny zakres procedur. Wiersz jest rysowany w *plikach źródłowych cs* projektu w lokalizacjach wymienionych w poniższej tabeli:

   |Lokalizacja w pliku źródłowym cs|Przykład lokalizacji wiersza|
   |---------------------------------|------------------------------|
   |Po zamknięciu konstrukcji deklaracji bloku|- Na końcu klasy, struktury, modułu, interfejsu lub wyli roku<br />- Po właściwości, funkcji lub podwłasce<br />- Nie między klauzulami get i set we właściwości|
   |Po zestawie konstrukcji jedno wierszowych|- Po instrukcjach importowania przed definicją typu w pliku klasy<br />-Po zmiennych zadeklarowanych w klasie, przed procedurami|
   |Po deklaracjach jedno wierszowych (deklaracjach na poziomie nieblokowym)|- Następujące instrukcje importu, dziedziczą instrukcje, deklaracje zmiennych, deklaracje zdarzeń, deklaracje delegatów i instrukcje deklarowania bibliotek DLL|

## <a name="block-structure-guides"></a>Prowadnice struktury bloków

Zaznacz te pola wyboru, aby wyświetlić kropkowane linie pionowe między nawiasami klamrowymi ( **{}** ) w kodzie. Następnie można łatwo zobaczyć poszczególne bloki kodu dla konstrukcji poziomu deklaracji i poziomu kodu.

## <a name="comments"></a>Komentarze

- Generowanie komentarzy dokumentacji XML dla ///

   Po wybraniu wstawia elementy XML dla komentarzy dokumentacji XML po wpisaniu `///` wprowadzenia komentarza. Aby uzyskać więcej informacji na temat dokumentacji XML, [zobacz Komentarze dokumentacji XML (Przewodnik programowania w języku C#).](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)

::: moniker range=">=vs-2019"

## <a name="inline-hints"></a>Wskazówki wbudowane

- Wskazówki dotyczące nazw parametrów wbudowanych 
    
    Po wybraniu wstawia wskazówki dotyczące nazw parametrów dla literałów, literałów rzutowania i wystąpienia obiektów przed każdym argumentem w wywołaniach funkcji.  
    
    ![Wskazówki dotyczące nazw parametrów w tekście dla języka CSharp](media/inline-parameter-name-hints-csharp.png)

- Wskazówki dotyczące typów w tekście 
    
    Gdy ta opcja jest zaznaczona, wstawia wskazówki dotyczące typów dla zmiennych z typami wywnioskować i typami parametrów lambda.  
    
    ![Wskazówki dotyczące typów w tekście dla języka CSharp](media/inline-type-hints-csharp.png)

## <a name="inheritance-margin"></a>Margines dziedziczenia 

- Po wybraniu opcja dodaje ikony do marginesów reprezentujących implementacje i przesłonięcia kodu. Kliknięcie ikon marginesu dziedziczenia spowoduje wyświetlenie opcji dziedziczenia, które można wybrać, aby przejść do.

    ![Margines dziedziczenia](media/inheritance-margin.png)

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [How to: Insert XML comments for documentation generation (Jak wstawić komentarze XML do generowania dokumentacji)](../../ide/reference/generate-xml-documentation-comments.md)
- [Komentarze dokumentacji XML (Przewodnik programowania w języku C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XML (Przewodnik po języku C#)](/dotnet/csharp/codedoc)
- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
