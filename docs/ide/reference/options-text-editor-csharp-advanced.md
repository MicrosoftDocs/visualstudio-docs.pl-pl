---
title: Opcje, edytor tekstu, C#, zaawansowane
ms.date: 08/12/2020
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: akhera99
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b8e515058b17205a65bab401c7b31c7205aa55bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88214666"
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane

Na stronie opcje **Zaawansowane** można modyfikować ustawienia formatowania edytora, refaktoryzacji kodu i komentarzy dokumentacji XML dla języka C#. Aby uzyskać dostęp do tej strony opcji **Tools**, wybierz  >  **Opcje**narzędzia, a następnie wybierz **Edytor tekstu**  >  **C#**  >  **Advanced**.

> [!NOTE]
> Nie wszystkie opcje mogą być wyświetlane w tym miejscu.

## <a name="analysis"></a>Analiza

- Analiza kodu na żywo lub zakres analizy w tle

   Skonfiguruj zakres analizy w tle dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [How to: Configure Live Code Analysis Scope for Managed Code](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Dyrektywy using

- Umieść dyrektywy "system" jako pierwsze podczas sortowania przy użyciu

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym po kliknięciu prawym przyciskiem myszy sortuje `using` dyrektywy i umieszcza przestrzenie nazw "system" w górnej części listy.

   Przed sortowaniem:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po sortowaniu:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Oddziel przy użyciu grupy dyrektywy

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym prawym przyciskiem myszy oddziela `using` dyrektywy przez wstawianie pustego wiersza między grupami dyrektyw, które mają tę samą główną przestrzeń nazw.

   Przed sortowaniem:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po sortowaniu:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

::: moniker range=">=vs-2019"                                              
- Sugeruj użycie dla typów w zestawach .NET Framework
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Sugeruj użycie dla typów w zestawach odwołań
::: moniker-end                                                            

- Sugeruj użycie dla typów w pakietach NuGet

   Po wybraniu tych opcji można wykonać [szybką akcję](../quick-actions.md) , aby zainstalować pakiet NuGet i dodać `using` dyrektywę dla typów bez odwołań.

   ![Szybka akcja instalacji pakietu NuGet w programie Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Wyróżnianie

- Wyróżnij odwołania do symbolu pod kursorem

   Gdy kursor jest umieszczony wewnątrz symbolu lub po kliknięciu symbolu, wszystkie wystąpienia tego symbolu w pliku kodu są wyróżnione.

## <a name="outlining"></a>Tworzenie konspektu

- Wejdź do trybu konspektu przy otwieraniu plików

   Po wybraniu automatycznie określa plik kodu, który tworzy zwijane bloki kodu. Przy pierwszym otwarciu pliku, bloki #regions bloków i nieaktywnych bloków kodu są zwijane.

- Pokaż separatory wierszy procedury

   Edytor tekstu wskazuje wizualny zakres procedur. Wiersz jest rysowany w plikach źródłowych *. cs* projektu w lokalizacjach wymienionych w poniższej tabeli:

   |Lokalizacja w pliku źródłowym. cs|Przykład lokalizacji wiersza|
   |---------------------------------|------------------------------|
   |Po zamknięciu konstrukcji deklaracji bloku|-Na końcu klasy, struktury, modułu, interfejsu lub wyliczenia<br />-Po właściwości, funkcji lub sub<br />-Nie między klauzulami get i Set we właściwości|
   |Po zestawie pojedynczych konstrukcji|-Po instrukcjach importu przed definicją typu w pliku klasy<br />-Po zmiennych zadeklarowanych w klasie przed wszelkimi procedurami|
   |Po deklaracjach pojedynczego wiersza (deklaracje na poziomie niebloku)|-Następujące instrukcje importu, instrukcje dziedziczenia, deklaracje zmiennych, deklaracje zdarzeń, deklaracje delegata i instrukcje dotyczące bibliotek DLL|

## <a name="block-structure-guides"></a>Prowadnice struktury blokowej

Zaznacz te pola wyboru, aby wyświetlić kropkowane linie pionowe między nawiasami klamrowymi ( **{}** ) w kodzie. Następnie można łatwo zobaczyć pojedyncze bloki kodu dla poziomu deklaracji i konstrukcji na poziomie kodu.

## <a name="editor-help"></a>Pomoc edytora
::: moniker range=">=vs-2019"
- Wskazówki dotyczące nazw parametrów wbudowanych 
    
    Po wybraniu wstawia wskazówki dotyczące nazw parametrów dla literałów, literałów rzutowania i wystąpień obiektów przed każdym argumentem w wywołaniach funkcji.  
    
    ![Wskazówki dotyczące nazwy parametru wbudowanego dla CSharp](media/inline-parameter-name-hints-csharp.png)
::: moniker-end
- Generuj komentarze dokumentacji XML dla///

   Po wybraniu Wstawia elementy XML dla komentarzy dokumentacji XML po wprowadzeniu `///` komentarza. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [Komentarze dokumentacji XML (Przewodnik programowania w języku C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: wstawianie komentarzy XML do generacji dokumentacji](../../ide/reference/generate-xml-documentation-comments.md)
- [Komentarze dokumentacji XML (Przewodnik programowania w języku C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XML (Przewodnik C#)](/dotnet/csharp/codedoc)
- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
