---
title: Podstawowe informacje o projekcie sieci Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95c9f7c530d50a7eb89ebe33fad3862f036972d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825611"
---
# <a name="web-project-essentials"></a>Podstawowe informacje dotyczące projektów internetowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekty sieci Web tworzą aplikacje sieci Web. Możesz użyć projektu sieci Web, aby utworzyć aplikację sieci Web, która ma inteligentne strony sieci Web. Inteligentna Strona sieci Web zawiera kod po stronie serwera, który renderuje stronę sieci Web na żądanie.  
  
 Używając tradycyjnych języków programowania, takich jak [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../includes/csprcs-md.md)] , możesz tworzyć inteligentne strony sieci Web, aby zbierać i przetwarzać informacje od użytkownika, przechowywać je w bazie danych i tak dalej.  
  
- Model związany z kodem kojarzy zależne pliki kodu źródłowego ze stronami sieci Web, które mają rozszerzenie. aspx lub. asmx. Na przykład Hello. aspx może mieć zależny plik kodu źródłowego hello.aspx.cs.  
  
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
  
- System projektu witryny sieci Web jest implementowany przez dodanie szablonów projektów i elementów i rejestrację [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] projektu.  
  
- System WAP jest implementowany jako podtyp projektu, nazywany również projektem. [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)]Projekt został poddany przez PODTYP WAP w celu utworzenia systemu WAP. Aby uzyskać więcej informacji na temat podtypów projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).  
  
- Inteligentna Strona sieci Web łączy kod HTML z językiem programowania po stronie serwera. Język po stronie serwera jest nazywany zawartym językiem. Aby zapewnić obsługę zawartego języka, system projektu sieci Web musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rodzinę interfejsów.  
  
  - Aby zapewnić obsługę zawartego języka w edytorze, usługa języka HTML musi odroczyć wyświetlanie zawartego w nim kodu języka do zawartej usługi językowej.  

  - Znaczniki błędów (Red squigglies) powinny zawsze być tworzone w podstawowym buforze edytora kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Projekty internetowe](../../extensibility/internals/web-projects.md)
