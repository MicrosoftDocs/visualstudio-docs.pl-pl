---
title: Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f9d3c3e8ddffb72b04a9ca2fc0ec4df5eaac150
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087420"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML

W tym temacie omówiono problemy z zabezpieczeniami, które należy znać podczas pracy z edytorem XML lub debugerze XSLT.

## <a name="xml-editor"></a>Edytor XML

 Edytor XML opiera się na edytorze tekstu programu Visual Studio. Opiera się na <xref:System.Xml> i <xref:System.Xml.Xsl> klasy do obsługi wielu procesów XML.

- Przekształcenia XSLT są wykonywane w nowej domenie aplikacji. Przekształcenia XSLT są *piaskownicy*; oznacza to, że zasady zabezpieczeń dostępu kodu komputera służy do określania ograniczone uprawnienia oparte na którym znajduje się arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mieć najbardziej ograniczone uprawnienia, a arkusze stylów skopiowany na dysk twardy, uruchom z pełnego zaufania.

- <xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest używana do kompilowania XSLT do języka pośredniego firmy Microsoft, aby zwiększyć wydajność w czasie wykonywania.

- Schematy, prowadzące do lokalizacji zewnętrznej w pliku wykazu są automatycznie pobierane po pierwszym załadowaniu edytora XML. <xref:System.Xml.Schema.XmlSchemaSet> Klasa jest używana do kompilowania schematów. Plik wykazu, który jest dostarczany za pomocą edytora XML nie ma łącza do zewnętrznych schematów. Użytkownik musi jawnie dodać odwołanie do zewnętrznych schematu przed edytora XML pliki do pobrania pliku schematu. Pobieranie HTTP można wyłączyć za pomocą **różne opcje narzędzi** strony edytora XML.

- Edytor XML używa <xref:System.Net> klasy do pobrania schematów

## <a name="xslt-debugger"></a>Debuger XSLT

 Debuger XSLT korzysta z aparatu debugowania zarządzanego programu Visual Studio i klas z <xref:System.Xml> i <xref:System.Xml.Xsl> przestrzeni nazw.

- Debuger XSLT uruchamia każde przekształcenie XSLT w domenie aplikacji w trybie piaskownicy. Zasady zabezpieczeń dostępu kodu na komputerze jest używana do określania ograniczonych uprawnień oparte na którym znajduje się arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mieć najbardziej ograniczone uprawnienia, a arkusze stylów skopiowany na dysk twardy, uruchom z pełnego zaufania.

- Arkusz stylów XSLT jest skompilowana przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.

- Ewaluator wyrażeń XSLT jest ładowany przez aparat debugowania zarządzanego. Aparat debugowania zarządzanego przyjęto założenie, że cały kod jest uruchamiany z komputera lokalnego użytkownika. W związku z tym <xref:System.Xml.Xsl.XslCompiledTransform> klasy pobiera plik XSLT do użytkownika komputera lokalnego. Możliwość, że podwyższenie poziomu w uprawnień do wykonywania może wystąpić skuteczność została osłabiona przez wykonywanie wszystkie przekształcenia XSLT w nowej domeny aplikacji z ograniczonymi uprawnieniami

## <a name="see-also"></a>Zobacz także

- [Domeny aplikacji](/dotnet/framework/app-domains/application-domains)