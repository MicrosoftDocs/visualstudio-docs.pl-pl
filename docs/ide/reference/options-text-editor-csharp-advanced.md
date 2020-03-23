---
title: Opcje, edytor tekstu, C#, zaawansowane
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d0e04a011612cdebebd244fc061981b713b858a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431491"
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane

Strona Opcje **zaawansowane** służy do modyfikowania ustawień formatowania edytora, refaktoryzacji kodu i komentarzy dokumentacji XML dla języka C#. Aby uzyskać dostęp do tej strony opcji, wybierz pozycję**Opcje** **narzędzi** > , a następnie wybierz pozycję **Edytor** > tekstu**C#** > **Zaawansowane**.

> [!NOTE]
> Nie wszystkie opcje mogą być wymienione tutaj.

## <a name="analysis"></a>Analiza

- Analiza kodu na żywo lub zakres analizy w tle

   Skonfiguruj zakres analizy w tle dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Korzystanie z dyrektyw

- Umieść dyrektywy "System" na pierwszym miejscu podczas sortowania za pomocą

   Po wybraniu tej opcji polecenie **Usuń i posortuj usings** w menu prawym przyciskiem myszy sortuje `using` dyrektywy i umieszcza obszary nazw "System" u góry listy.

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

- Oddzielanie grup dyrektyw przy użyciu

   Po wybraniu tej opcji polecenie **Usuń i sortuj usings** w menu po kliknięciu prawym przyciskiem myszy oddziela `using` dyrektywy, wstawiając pustą linię między grupami dyrektyw, które mają ten sam główny obszar nazw.

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

- Sugerowanie użycia typów w zestawach programu .NET Framework
- Sugerowanie użycia typów w pakietach NuGet

   Gdy te opcje są zaznaczone, [szybka akcja](../quick-actions.md) jest dostępna `using` do zainstalowania pakietu NuGet i dodać dyrektywę dla typów bez odwołań.

   ![Szybka akcja instalowania pakietu NuGet w programie Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Wyróżnianie

- Wyróżnianie odniesień do symbolu pod kursorem

   Gdy kursor jest umieszczony wewnątrz symbolu lub po kliknięciu symbolu, wszystkie wystąpienia tego symbolu w pliku kodu są podświetlone.

## <a name="outlining"></a>Tworzenie konspektu

- Wprowadzanie trybu tworzenia po otwarciu plików

   Gdy ta opcja jest zaznaczona, automatycznie konspektuje plik kodu, który tworzy zwijane bloki kodu. Przy pierwszym otwarciu pliku #regions bloków i nieaktywnych bloków kodu zwijają się.

- Pokaż separatory linii procedury

   Edytor tekstu wskazuje wizualny zakres procedur. Wiersz jest rysowany w plikach źródłowych *.cs* projektu w lokalizacjach wymienionych w poniższej tabeli:

   |Lokalizacja w pliku źródłowym .cs|Przykład lokalizacji wiersza|
   |---------------------------------|------------------------------|
   |Po zamknięciu konstrukcji deklaracji bloku|- Na końcu klasy, struktury, modułu, interfejsu lub wyliczenia<br />- Po właściwości, funkcji lub sub<br />- Nie między get i set klauzule w właściwości|
   |Po zestawie konstrukcji jednoliniowych|- Po instrukcjach importu przed definicją typu w pliku klasy<br />- Po zmiennych zadeklarowanych w klasie, przed jakimikolwiek procedurami|
   |Po deklaracjach jednowierszowych (deklaracje na poziomie nieblokowym)|- Po instrukcji importu, dziedziczy instrukcje, deklaracje zmiennych, deklaracje zdarzeń, deklaracje delegata i dll zadeklarować instrukcje|

## <a name="block-structure-guides"></a>Prowadnice struktury bloków

Zaznacz te pola wyboru, aby wyświetlić kropkowane pionowe linie między nawiasami klamrowymi (**{}**) w kodzie. Następnie można łatwo wyświetlić poszczególne bloki kodu dla poziomu deklaracji i konstrukcji poziomu kodu.

## <a name="editor-help"></a>Pomoc edytora

- Generowanie komentarzy dokumentacji XML dla ///

   Gdy ta opcja jest zaznaczona, po wpisaniu `///` komentarza wstawia elementy XML dla komentarzy dokumentacji XML. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [Komentarze do dokumentacji XML (Przewodnik po programowaniu w języku C#).](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)

## <a name="see-also"></a>Zobacz też

- [Jak: Wstawianie komentarzy XML do generowania dokumentacji](../../ide/reference/generate-xml-documentation-comments.md)
- [Komentarze dokumentacji XML (Przewodnik programowania w języku C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XML (Przewodnik języka C#)](/dotnet/csharp/codedoc)
- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
