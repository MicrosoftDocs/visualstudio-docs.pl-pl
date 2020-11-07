---
title: Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML
description: Informacje o kwestiach dotyczących zabezpieczeń podczas pracy z danymi XML w edytorze XML lub debugerze XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9e98e18e3e01f53afa6b0a9ea3bdec94f2186f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351352"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML

W tym temacie omówiono problemy związane z zabezpieczeniami, które należy znać podczas pracy z edytorem XML lub debugerem XSLT.

## <a name="xml-editor"></a>Edytor XML

Edytor XML jest oparty na edytorze tekstu programu Visual Studio. Opiera się on na <xref:System.Xml> <xref:System.Xml.Xsl> klasach i obsługujących wiele procesów XML.

- Przekształcenia XSLT są wykonywane w nowej domenie aplikacji. Przekształcenia XSLT są w *trybie piaskownicy* ; oznacza to, że zasady zabezpieczeń dostępu kodu komputera są używane do określania ograniczonych uprawnień na podstawie lokalizacji arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mają najbardziej ograniczone uprawnienia, a arkusze stylów skopiowane na dysk twardy są uruchamiane z pełnym zaufaniem.

- <xref:System.Xml.Xsl.XslCompiledTransform>Klasa jest używana do kompilowania XSLT do języka pośredniego firmy Microsoft w celu zwiększenia wydajności podczas wykonywania.

- Schematy wskazujące lokalizację zewnętrzną w pliku wykazu są automatycznie pobierane po pierwszym załadowaniu edytora XML. <xref:System.Xml.Schema.XmlSchemaSet>Klasa jest używana do kompilowania schematów. Plik wykazu, który jest dostarczany z edytorem XML, nie zawiera linków do żadnych zewnętrznych schematów. Użytkownik musi jawnie dodać odwołanie do zewnętrznego schematu, zanim Edytor XML pobierze plik schematu. Pobieranie HTTP można wyłączyć za pomocą strony **Opcje narzędzi dodatkowych** dla edytora XML.

- Edytor XML używa <xref:System.Net> klas do pobierania schematów

## <a name="xslt-debugger"></a>Debuger XSLT

Debuger XSLT wykorzystuje zarządzane aparaty debugowania programu Visual Studio i klasy z <xref:System.Xml> <xref:System.Xml.Xsl> przestrzeni nazw i.

- Debuger XSLT uruchamia każdą transformację XSLT w domenie aplikacji w trybie piaskownicy. Zasady zabezpieczeń dostępu kodu komputera są używane do określania ograniczonych uprawnień na podstawie lokalizacji arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mają najbardziej ograniczone uprawnienia, a arkusze stylów skopiowane na dysk twardy są uruchamiane z pełnym zaufaniem.

- Arkusz stylów XSLT jest kompilowany przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.

- Ewaluatora wyrażeń XSLT jest ładowany przez zarządzany aparat debugowania. Zarządzany aparat debugowania zakłada, że cały kod jest uruchamiany z komputera lokalnego użytkownika. W związku z tym <xref:System.Xml.Xsl.XslCompiledTransform> Klasa pobiera plik XSLT na komputer lokalny użytkownika. Możliwe, że może wystąpić podniesienie uprawnień w wykonywaniu, przez wykonanie wszystkich transformacji XSLT w nowej domenie aplikacji z ograniczonymi uprawnieniami

## <a name="see-also"></a>Zobacz też

- [Domeny aplikacji](/dotnet/framework/app-domains/application-domains)