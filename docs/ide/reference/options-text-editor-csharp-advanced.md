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
ms.openlocfilehash: c2f4c01a627fb2cd1b581331dd086e2d783d475f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596232"
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane

Na stronie opcje **Zaawansowane** można modyfikować ustawienia formatowania edytora, refaktoryzacji kodu i komentarzy dokumentacji XML C#. Aby uzyskać dostęp do tej strony opcji, wybierz pozycję **narzędzia** > **Opcje**, a następnie wybierz **C#** pozycję **Edytor tekstu** >  > **Zaawansowane**.

> [!NOTE]
> Nie wszystkie opcje mogą być wyświetlane w tym miejscu.

## <a name="analysis"></a>Analiza

- Włączanie pełnej analizy rozwiązania

   Włącza analizę kodu dla wszystkich plików w rozwiązaniu, a nie tylko otwartych plików kodu. Aby uzyskać więcej informacji, zobacz [Pełna analiza rozwiązania](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Dyrektywy using

- Umieść dyrektywy "system" jako pierwsze podczas sortowania przy użyciu

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym prawym przyciskiem myszy sortuje dyrektywy `using` i umieszcza przestrzenie nazw "system" na początku listy.

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

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym prawym przyciskiem myszy oddziela dyrektywy `using`, wstawiając pusty wiersz między grupami dyrektyw, które mają tę samą główną przestrzeń nazw.

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

- Sugeruj użycie dla typów w zestawach odwołań
- Sugeruj użycie dla typów w pakietach NuGet

   Po wybraniu tych opcji można wykonać [szybką akcję](../quick-actions.md) , aby zainstalować pakiet NuGet i dodać dyrektywę `using` dla typów bez odwołań.

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

- Generuj komentarze dokumentacji XML dla///

   Po wybraniu Wstawia elementy XML dla komentarzy dokumentacji XML po wpisaniu `///` wprowadzenia komentarza. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [Komentarze dokumentacjiC# XML (Przewodnik programowania)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: wstawianie komentarzy XML do generacji dokumentacji](../../ide/reference/generate-xml-documentation-comments.md)
- [Komentarze dokumentacji XML (C# Przewodnik programowania)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XMLC# (Przewodnik)](/dotnet/csharp/codedoc)
- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
