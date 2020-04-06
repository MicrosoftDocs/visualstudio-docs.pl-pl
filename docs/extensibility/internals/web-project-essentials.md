---
title: Podstawowe informacje o projekcie internetowym | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703549"
---
# <a name="web-project-essentials"></a>Podstawowe informacje dotyczące projektów internetowych
Projekty sieci Web tworzą aplikacje sieci Web. Za pomocą projektu sieci Web można utworzyć aplikację sieci Web zawierającą inteligentne strony sieci Web. Inteligentna strona sieci Web ma kod po stronie serwera, który renderuje stronę sieci Web na żądanie.

 Korzystając z tradycyjnych języków [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] programowania, takich jak lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], można tworzyć inteligentne strony sieci Web do zbierania i przetwarzania informacji od użytkownika, przechowywania ich w bazie danych i tak dalej.

- Model związany z kodem kojarzy zależne pliki kodu źródłowego ze stronami sieci Web z rozszerzeniem pliku .aspx lub .asmx. Na przykład hello.aspx może mieć zależny plik kodu źródłowego hello.aspx.cs.

- Kod po stronie serwera skojarzony ze inteligentną stroną sieci Web jest kompilowany do pliku wykonywalnego znajdującego się w folderze witryny sieci Web /bin.

- Dodatkowe pliki kodu źródłowego, takie jak klasy pomocnicze, które nie są skojarzone z określoną stroną sieci Web, znajdują się w folderze /App_Code witryny sieci Web.

  - Projekt witryny sieci Web (WSP) generuje jeden plik wykonywalny dla każdej inteligentnej strony sieci Web. Dodatkowe pliki wykonywalne są generowane z dowolnych plików kodu źródłowego w /App_Code folderze.

  - Projekt aplikacji sieci Web (WAP) tworzy pojedynczy plik wykonywalny, który łączy kod dla wszystkich inteligentnych stron sieci Web, a także wszystkie pliki źródłowe w /App_Code folderze.

- Plik rozwiązania dla projektu sieci Web znajduje się oddzielnie od samej witryny sieci Web. Domyślnie pliki rozwiązań znajdują się\\w folderze \Documents and Settings*YourAccount*\My\\Documents\\*\<Visual Studio ####>* \Projects*YourWebSite*.

  > [!NOTE]
  > Jeśli chcesz zachować plik rozwiązania w witrynie sieci Web, po prostu przenieś go tam i otwórz ponownie.

- Jeśli otworzysz witrynę sieci Web, która nie ma pliku rozwiązania w programie Visual Studio, automatycznie generowany jest dla niego nowy plik rozwiązania.

- Projekty sieci Web nie mają plików projektu. Informacje o projekcie są przechowywane w pliku rozwiązania, pliku web.config i w innych miejscach.

- Dodanie właściwości globalnych do projektu sieci Web powoduje automatyczne utworzenie pliku magazynu w folderze rozwiązanie projektu sieci Web.

- Inteligentną stronę sieci Web można skojarzyć z językiem programowania \<po stronie serwera przy użyciu dyrektywy Page lub tagu > skryptu runat="server".

- Ponadto strony sieci Web mogą mieć dowolną liczbę bloków skryptów po stronie klienta napisanych w dowolnym języku skryptów.

- System projektu witryny sieci Web jest implementowany przez dodanie [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] szablonów projektów i elementów oraz rejestrację do projektu.

- System WAP jest realizowany jako podtyp projektu, nazywany również smakiem projektu. Projekt [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] jest aromatyzowane przez podtyp WAP do tworzenia systemu WAP. Aby uzyskać więcej informacji na temat podtypów projektu, zobacz [Podtypy projektu](../../extensibility/internals/project-subtypes.md).

- Inteligentna strona sieci Web łączy kod HTML z językiem programowania po stronie serwera. Język po stronie serwera jest nazywany zawartym językiem. Aby obsługiwać zawarty język, system projektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> sieci Web musi implementować rodzinę interfejsów.

  - Aby obsługiwać zawarty język w edytorze, usługa języka HTML musi odroczyć wyświetlanie kodu języka zawartego w zamkniętej usłudze języka.

  - Znaczniki błędów (czerwone faliste) powinny być zawsze tworzone w buforze podstawowym edytora kodu.

## <a name="see-also"></a>Zobacz też
- [Projekty internetowe](../../extensibility/internals/web-projects.md)
