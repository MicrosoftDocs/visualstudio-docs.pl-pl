---
title: Opcje, edytor tekstu, C#, zaawansowane
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7cfbc6d57e5bfd3c6a8f317967448039a9b3f5e4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670718"
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane

Użyj **zaawansowane** Strona opcji, aby modyfikować ustawienia formatowania edytora, refaktoryzacji kodu i komentarze dokumentacji XML dla języka C#. Dostępu do tej opcji strony, wybierz **narzędzia** > **opcje**, a następnie wybierz **edytora tekstów** > **C#**  >  **Zaawansowane**.

> [!NOTE]
> Nie wszystkie opcje mogą być wymienione w tym miejscu.

## <a name="analysis"></a>Analiza

- Włączanie pełnej analizy rozwiązania

   Włącza analizę kodu dla wszystkich plików w rozwiązaniu, nie wystarczy otworzyć plików kodu. Aby uzyskać więcej informacji, zobacz [pełnej analizy rozwiązania](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Dyrektywy Using

- Umieść najpierw dyrektywy "System" podczas sortowania deklaracji Using

   Po wybraniu **Usuń i Sortuj wyrażenia Using** w sortuje menu kliknij prawym przyciskiem myszy polecenie `using` dyrektywy i miejsc przestrzeni nazw "System" w górnej części listy.

   Przed rozpoczęciem sortowania:

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
   
- Oddziel grupy dyrektywy using

   Po wybraniu **Usuń i Sortuj wyrażenia Using** oddziela polecenia w menu kliknij prawym przyciskiem myszy `using` dyrektyw, wstawiając pusty wiersz między grupami dyrektyw, które mają ten sam głównej przestrzeni nazw.

   Przed rozpoczęciem sortowania:

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
   
- Sugeruj dyrektywy Using dla typów w zestawach referencyjnych 
- Sugeruj dyrektywy Using dla typów w pakietach NuGet 

   Po wybraniu tych opcji [szybka akcja](../quick-actions.md) jest dostępna zainstalować pakiet NuGet i dodać `using` dyrektywy dla typów bez odwołań.

   ![Szybkie działanie, aby zainstalować pakiet NuGet w programie Visual Studio](media/nuget-lightbulb.png)
  
## <a name="highlighting"></a>Wyróżnianie

- Wyróżnij odwołania do symbolu pod kursorem

   Gdy kursor znajduje się wewnątrz symbolu lub po kliknięciu symbolu, zostały wyróżnione wszystkich wystąpień symbolu w pliku kodu.

## <a name="outlining"></a>Tworzenie konspektu

- Przejdź do trybu konspektu po otwarciu plików

   Po wybraniu automatycznie przedstawia plik kodu, który tworzy zwijany bloków kodu. Przy pierwszym otwarciu pliku #regions bloków i bloków nieaktywnego kodu Zwiń.

- Pokaż separatory wierszy procedury

   Edytor tekstu wskazuje zakres visual procedur. Linia jest rysowana *.vb* pliki źródłowe projektu w lokalizacjach wymienione w poniższej tabeli:

   |Lokalizacja w pliku źródłowym .vb|Przykład lokalizację wiersza|
   |---------------------------------|------------------------------|
   |Po zamknięciu bloku konstrukcja deklaracji|-Na końcu klasy, struktury, moduł, interfejs lub wyliczenie<br />-After właściwości, funkcji lub sub<br />-Nie między get i set klauzule we właściwości|
   |Po zestaw konstrukcji w jednym wierszu|-After instrukcje importowania, przed definicją typu w pliku klasy<br />-After zmienne zadeklarowane w klasie, zanim wszelkie procedury|
   |Po jednym wierszu deklaracji (-block deklaracje poziomu)|— Następujące instrukcje importu dziedziczy instrukcji, deklaracji zmiennych, deklaracji zdarzeń, delegat deklaracje i biblioteki DLL zadeklarować instrukcji|

## <a name="editor-help"></a>Pomoc Edytora

- Generowanie komentarzy dokumentacji XML dla / / /

   Po wybraniu Wstawia elementy XML dla komentarzy dokumentacji XML po wpisaniu `///` wprowadzenie komentarza. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [komentarze dokumentacji XML (C# Programming Guide)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Zobacz także

- [Porady: wstawianie komentarzy XML do generowania dokumentacji](../../ide/reference/generate-xml-documentation-comments.md)
- [Komentarze dokumentacji XML (C# Programming Guide)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu przy użyciu komentarzy XML (Przewodnik C#)](/dotnet/csharp/codedoc)
- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
