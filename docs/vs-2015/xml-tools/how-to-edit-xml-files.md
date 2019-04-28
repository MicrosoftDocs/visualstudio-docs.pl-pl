---
title: 'Instrukcje: Edytowanie plików XML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 60b94274404c82695628dc72bd88bdf48145b7c2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443442"
---
# <a name="how-to-edit-xml-files"></a>Instrukcje: Edytowanie plików XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML jest nowym edytorze plików XML. Może służyć autonomiczny plik XML lub plik skojarzony z projektu programu Visual Studio. Edytor XML jest skojarzony z następujących rozszerzeń pliku: .config, .dtd, XML i XSD, a także .xdr, XSL, .xslt i .vssettings. Edytor XML jest powiązany z pliku innego typu ma nie określonych Edytor zarejestrowany i zawiera zawartość DTD lub XML.  
  
> [!NOTE]
> XHTML dokumentów są obsługiwane w edytorze HTML.  
  
### <a name="to-edit-an-xml-file"></a>Aby edytować plik XML  
  
1. Kliknij dwukrotnie plik, który chcesz edytować.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>Aby dodać nowy plik XML do projektu  
  
1. Z **projektu** menu, wybierz opcję **Dodaj nowy element**.  
  
2. Wybierz **pliku XML** z **szablony** okienka.  
  
3. Wprowadź nazwę pliku w **nazwa** pole i naciśnij klawisz **Dodaj**.  
  
     Plik XML jest dodawany do projektu i otworzyć w edytorze XML. Ten plik zawiera domyślne deklaracji XML, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>Aby dodać istniejący plik XML do projektu  
  
1. Z **projektu** menu, wybierz opcję **Dodaj istniejący element**.  
  
     **Dodaj istniejący element** pojawi się okno dialogowe.  
  
2. Wybierz plik XML i naciśnij klawisz **Dodaj**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>Aby utworzyć nowy plik XML lub XSLT  
  
1. Z **pliku** menu, wybierz opcję **New**.  
  
     **Nowy plik** pojawi się okno dialogowe.  
  
2. Wybierz **pliku XML** Aby utworzyć nowy plik XML; lub wybierz **pliku XSLT** do utworzenia nowego arkusza stylów XSLT.  
  
3. Kliknij przycisk **Otwórz**.  
  
### <a name="to-create-a-project-for-xml-files"></a>Aby utworzyć projekt dla plików XML  
  
1. Z **pliku** menu, wybierz opcję **New**, a następnie wybierz pozycję **projektu**.  
  
     **Nowy projekt** pojawi się okno dialogowe.  
  
2. Wybierz język kodu, co pozwala wybierz **pusty projekt**i kliknij przycisk **OK**.  
  
3. Dodaj pliki XML do projektu.  
  
     Edytor XML znajduje schematy dodanych do tego projektu i używa ich do walidacji i IntelliSense w dowolnym XML, schematu lub pliki XSLT, które możesz edytować, gdy ten projekt jest otwarty.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)   
 [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)   
 [Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
