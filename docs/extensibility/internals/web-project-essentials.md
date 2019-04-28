---
title: Podstawowe informacje dotyczące projektów internetowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30ffd684eb6527ee73e54cc590dc3e4b1d3c51d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429351"
---
# <a name="web-project-essentials"></a>Podstawowe informacje dotyczące projektów internetowych
Projekty sieci Web tworzyć aplikacje sieci Web. Projekt sieci Web można użyć, aby utworzyć aplikację internetową, która ma inteligentne strony sieci Web. Inteligentne strony sieci Web zawiera kod po stronie serwera, który renderuje stronę sieci Web na żądanie.

 Przy użyciu tradycyjnych językach programowania, takich jak [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], można tworzyć inteligentne strony sieci Web do zbierania i przetwarzania informacji od użytkownika, zapisz go w bazie danych i tak dalej.

- Model związanym z kodem kojarzy plików kodu źródłowego zależne ze stronami sieci Web, w których .aspx rozszerzenia pliku lub .asmx. Na przykład hello.aspx może być hello.aspx.cs pliku kodu źródłowego zależnych.

- Kod po stronie serwera, skojarzone ze stroną sieci Web inteligentne jest kompilowany do pliku wykonywalnego, który znajduje się w katalogu/bin witryny sieci Web.

- Pliki kodu dodatkowe źródła, takich jak klasy pomocnika, które nie są skojarzone z określonej strony sieci Web znajdują się w folderze /App_Code witryny sieci Web.

  - Projekt witryny sieci Web (WSP) generuje jednego pliku wykonywalnego, dla każdej inteligentne strony sieci Web. Dodatkowe pliki wykonywalne są generowane na podstawie żadnych plików kodu źródłowego w folderze /App_Code.

  - Projekt aplikacji sieci Web (WAP) tworzy jednej plik wykonywalny, który łączy kod dla wszystkich stron sieci Web inteligentnego, a także wszystkich plików źródłowych z folderu /App_Code.

- Niezależnie od w witrynie sieci Web znajduje się plik rozwiązania dla projektu sieci Web. Domyślnie pliki rozwiązania znajdują się w \Documents and Settings\\*Twojekonto*\My dokumenty\\*\<programu Visual Studio ### >* \Projects\\ *YourWebSite*.

  > [!NOTE]
  > Jeśli chcesz zachować plik rozwiązania z witryny sieci Web, po prostu przesuń istnieje i otwórz go ponownie.

- Po otwarciu witryny sieci Web, która nie ma rozwiązania pliku w programie Visual Studio, nowy plik rozwiązania jest generowane automatycznie dla niego.

- Projekty sieci Web nie ma żadnych plików projektu. Informacje o projekcie są przechowywane w pliku rozwiązania, w pliku web.config i w innych miejscach.

- Dodanie właściwości globalne do projektu sieci Web automatycznie tworzy plik magazynu w folderze rozwiązania projektu sieci Web.

- Inteligentne strony sieci Web mogą być skojarzone z językiem programowania po stronie serwera za pomocą dyrektywy strony lub \<skryptu runat = "server" > tag.

- Ponadto stron sieci Web może mieć dowolną liczbę bloków skryptów po stronie klienta, napisane w dowolnym języku skryptów.

- System projektu witryny sieci Web jest implementowany przez dodanie szablonów projektów i elementów i rejestracji w celu [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projektu.

- System proxy aplikacji sieci Web jest wdrażany jako podtypem projektu, jest określana skrótem podtypem projektu. [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projektu jest składni, podtypu WAP tworzenia systemu WAP. Aby uzyskać więcej informacji na temat podtypy projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

- Inteligentne strony sieci Web łączy HTML w języku programowania po stronie serwera. Język po stronie serwera jest nazywany językowych zawarte. Aby umożliwić obsługę ograniczonego języka, system projektu sieci Web musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rodziny interfejsów.

  - Aby zapewnić obsługę języka zawartych w edytorze, usługa języka HTML musi Odrocz wyświetlające kod języka zawartej z usługą językowych zawarte.

  - Znaczniki błędów (czerwony squigglies) zawsze powinny być tworzone w edytorze kodu podstawowego buforu.

## <a name="see-also"></a>Zobacz też
- [Projekty internetowe](../../extensibility/internals/web-projects.md)