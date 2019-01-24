---
title: Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 804bc90e48a666c3eb4ea38abb01d7be0a50290e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764989"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
W tym temacie omówiono problemy z zabezpieczeniami, które należy znać podczas pracy z edytorem XML lub debugerze XSLT.  
  
## <a name="xml-editor"></a>Edytor XML  
 Edytor XML opiera się na edytorze tekstu programu Visual Studio. Opiera się na <xref:System.Xml> i <xref:System.Xml.Xsl> klasy do obsługi wielu procesów XML.  
  
-   Przekształcenia XSLT są wykonywane w nowej domenie aplikacji. Przekształcenia XSLT są *piaskownicy*; oznacza to, że zasady zabezpieczeń dostępu kodu komputera służy do określania ograniczone uprawnienia oparte na którym znajduje się arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mieć najbardziej ograniczone uprawnienia, a arkusze stylów skopiowany na dysk twardy, uruchom z pełnego zaufania.  
  
-   <xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest używana do kompilowania XSLT do języka pośredniego firmy Microsoft, aby zwiększyć wydajność w czasie wykonywania.  
  
-   Schematy, prowadzące do lokalizacji zewnętrznej w pliku wykazu są automatycznie pobierane po pierwszym załadowaniu edytora XML. <xref:System.Xml.Schema.XmlSchemaSet> Klasa jest używana do kompilowania schematów. Plik wykazu, który jest dostarczany za pomocą edytora XML nie ma łącza do zewnętrznych schematów. Użytkownik musi jawnie dodać odwołanie do zewnętrznych schematu przed edytora XML pliki do pobrania pliku schematu. Pobieranie HTTP można wyłączyć za pomocą **różne opcje narzędzi** strony edytora XML.  
  
-   Edytor XML używa <xref:System.Net> klasy do pobrania schematów  
  
## <a name="xslt-debugger"></a>Debuger XSLT  
 Debuger XSLT korzysta z aparatu debugowania zarządzanego programu Visual Studio i klas z <xref:System.Xml> i <xref:System.Xml.Xsl> przestrzeni nazw.  
  
-   Debuger XSLT uruchamia każde przekształcenie XSLT w domenie aplikacji w trybie piaskownicy. Zasady zabezpieczeń dostępu kodu na komputerze jest używana do określania ograniczonych uprawnień oparte na którym znajduje się arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mieć najbardziej ograniczone uprawnienia, a arkusze stylów skopiowany na dysk twardy, uruchom z pełnego zaufania.  
  
-   Arkusz stylów XSLT jest skompilowana przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
-   Ewaluator wyrażeń XSLT jest ładowany przez aparat debugowania zarządzanego. Aparat debugowania zarządzanego przyjęto założenie, że cały kod jest uruchamiany z komputera lokalnego użytkownika. W związku z tym <xref:System.Xml.Xsl.XslCompiledTransform> klasy pobiera plik XSLT do użytkownika komputera lokalnego. Możliwość, że podwyższenie poziomu w uprawnień do wykonywania może wystąpić skuteczność została osłabiona przez wykonywanie wszystkie przekształcenia XSLT w nowej domeny aplikacji z ograniczonymi uprawnieniami  
  
## <a name="see-also"></a>Zobacz też  
 [Domeny aplikacji](http://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)
