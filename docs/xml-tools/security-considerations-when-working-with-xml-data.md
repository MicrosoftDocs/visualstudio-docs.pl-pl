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
ms.openlocfilehash: 5fe4ec69f879478566cce8d077bb66b34da86f3d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926765"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML

W tym temacie omówiono problemy związane z zabezpieczeniami, które należy znać podczas pracy z edytorem XML lub debugerem XSLT.

## <a name="xml-editor"></a>Edytor XML

Edytor XML jest oparty na edytorze tekstu programu Visual Studio. Opiera się on na <xref:System.Xml> klasach i <xref:System.Xml.Xsl> obsługujących wiele procesów XML.

- Przekształcenia XSLT są wykonywane w nowej domenie aplikacji. Przekształcenia XSLT są w *trybie piaskownicy*; oznacza to, że zasady zabezpieczeń dostępu kodu komputera są używane do określania ograniczonych uprawnień na podstawie lokalizacji arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mają najbardziej ograniczone uprawnienia, a arkusze stylów skopiowane na dysk twardy są uruchamiane z pełnym zaufaniem.

- <xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest używana do kompilowania XSLT do języka pośredniego firmy Microsoft w celu zwiększenia wydajności podczas wykonywania.

- Schematy wskazujące lokalizację zewnętrzną w pliku wykazu są automatycznie pobierane po pierwszym załadowaniu edytora XML. <xref:System.Xml.Schema.XmlSchemaSet> Klasa jest używana do kompilowania schematów. Plik wykazu, który jest dostarczany z edytorem XML, nie zawiera linków do żadnych zewnętrznych schematów. Użytkownik musi jawnie dodać odwołanie do zewnętrznego schematu, zanim Edytor XML pobierze plik schematu. Pobieranie HTTP można wyłączyć za pomocą strony **Opcje narzędzi dodatkowych** dla edytora XML.

- Edytor XML używa <xref:System.Net> klas do pobierania schematów

## <a name="xslt-debugger"></a>Debuger XSLT

Debuger XSLT wykorzystuje zarządzane aparaty debugowania programu Visual Studio i klasy z <xref:System.Xml> przestrzeni nazw i. <xref:System.Xml.Xsl>

- Debuger XSLT uruchamia każdą transformację XSLT w domenie aplikacji w trybie piaskownicy. Zasady zabezpieczeń dostępu kodu komputera są używane do określania ograniczonych uprawnień na podstawie lokalizacji arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mają najbardziej ograniczone uprawnienia, a arkusze stylów skopiowane na dysk twardy są uruchamiane z pełnym zaufaniem.

- Arkusz stylów XSLT jest kompilowany przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.

- Ewaluatora wyrażeń XSLT jest ładowany przez zarządzany aparat debugowania. Zarządzany aparat debugowania zakłada, że cały kod jest uruchamiany z komputera lokalnego użytkownika. W związku z <xref:System.Xml.Xsl.XslCompiledTransform> tym Klasa pobiera plik XSLT na komputer lokalny użytkownika. Możliwe, że może wystąpić podniesienie uprawnień w wykonywaniu, przez wykonanie wszystkich transformacji XSLT w nowej domenie aplikacji z ograniczonymi uprawnieniami

## <a name="see-also"></a>Zobacz także

- [Domeny aplikacji](/dotnet/framework/app-domains/application-domains)