---
title: Podstawowe informacje o projekcie sieci Web | Microsoft Docs
description: Zapoznaj się ze szczegółami wewnętrznymi dotyczącymi działania projektów sieci Web w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9442dcdd460e1213c3c07ee87a5ea2e0d7099072
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085705"
---
# <a name="web-project-essentials"></a>Podstawowe informacje dotyczące projektów internetowych
Projekty sieci Web tworzą aplikacje sieci Web. Możesz użyć projektu sieci Web, aby utworzyć aplikację sieci Web, która ma inteligentne strony sieci Web. Inteligentna Strona sieci Web zawiera kod po stronie serwera, który renderuje stronę sieci Web na żądanie.

 Używając tradycyjnych języków programowania, takich jak [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] , możesz tworzyć inteligentne strony sieci Web, aby zbierać i przetwarzać informacje od użytkownika, przechowywać je w bazie danych i tak dalej.

- Model związany z kodem kojarzy zależne pliki kodu źródłowego ze stronami sieci Web, które mają rozszerzenie. aspx lub. asmx. Na przykład Witaj. aspx może być zależny od pliku kodu źródłowego Hello. aspx. cs.

- Kod po stronie serwera skojarzony z inteligentną stroną sieci Web jest kompilowany do pliku wykonywalnego, który znajduje się w folderze/bin. witryny sieci Web.

- Dodatkowe pliki kodu źródłowego, takie jak klasy pomocnika, które nie są skojarzone z konkretną stroną sieci Web, znajdują się w folderze witryna sieci Web/App_Code.

  - Projekt witryny sieci Web (WSP) generuje jeden plik wykonywalny dla każdej z inteligentnych stron sieci Web. Dodatkowe pliki wykonywalne są generowane na podstawie dowolnych plików kodu źródłowego w folderze/App_Code.

  - Projekt aplikacji sieci Web (WAP) tworzy pojedynczy plik wykonywalny, który łączy kod dla wszystkich inteligentnych stron sieci Web, a także wszystkie pliki źródłowe w folderze/App_Code.

- Plik rozwiązania dla projektu sieci Web znajduje się niezależnie od samej witryny sieci Web. Domyślnie pliki rozwiązania znajdują się w obszarze \Documents and Settings \\ *YourAccount*\Moje Documents \\ *\<Visual Studio ####>* \Projects \\ *YourWebSite*.

  > [!NOTE]
  > Jeśli chcesz zachować plik rozwiązania z witryną sieci Web, wystarczy przenieść go tam i otworzyć ponownie.

- Jeśli otworzysz witrynę sieci Web, która nie ma pliku rozwiązania w programie Visual Studio, zostanie automatycznie wygenerowany nowy plik rozwiązania.

- Projekty sieci Web nie mają plików projektu. Informacje o projekcie są przechowywane w pliku rozwiązania, pliku web.config i innym miejscu.

- Dodanie globalnych właściwości do projektu sieci Web powoduje automatyczne utworzenie pliku magazynu w folderze rozwiązania projektu sieci Web.

- Inteligentna Strona sieci Web może być skojarzona z językiem programowania po stronie serwera za pomocą dyrektywy Page lub \<script runat="server"> tag.

- Ponadto strony sieci Web mogą zawierać dowolną liczbę bloków skryptów po stronie klienta, które są zapisywane w dowolnym języku skryptowym.

- System projektu witryny sieci Web jest implementowany przez dodanie szablonów projektów i elementów i rejestrację [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projektu.

- System WAP jest implementowany jako podtyp projektu, nazywany również projektem. [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]Projekt został poddany przez PODTYP WAP w celu utworzenia systemu WAP. Aby uzyskać więcej informacji na temat podtypów projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

- Inteligentna Strona sieci Web łączy kod HTML z językiem programowania po stronie serwera. Język po stronie serwera jest nazywany zawartym językiem. Aby zapewnić obsługę zawartego języka, system projektu sieci Web musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rodzinę interfejsów.

  - Aby zapewnić obsługę zawartego języka w edytorze, usługa języka HTML musi odroczyć wyświetlanie zawartego w nim kodu języka do zawartej usługi językowej.

  - Znaczniki błędów (Red squigglies) powinny zawsze być tworzone w podstawowym buforze edytora kodu.

## <a name="see-also"></a>Zobacz też
- [Projekty internetowe](../../extensibility/internals/web-projects.md)
