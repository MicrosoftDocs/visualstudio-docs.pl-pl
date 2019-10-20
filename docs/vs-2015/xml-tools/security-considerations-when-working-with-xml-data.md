---
title: Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 491e8cf8f9441180e66259ed295e04e8a1a90493
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656139"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Zagadnienia dotyczące zabezpieczeń podczas pracy z danymi XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono problemy związane z zabezpieczeniami, które należy znać podczas pracy z edytorem XML lub debugerem XSLT.

## <a name="xml-editor"></a>Edytor XML
 Edytor XML jest oparty na edytorze tekstu programu Visual Studio. Zależy to od klas <xref:System.Xml> i <xref:System.Xml.Xsl> do obsługi wielu procesów XML.

- Przekształcenia XSLT są wykonywane w nowej domenie aplikacji. Przekształcenia XSLT są w *trybie piaskownicy*; oznacza to, że zasady zabezpieczeń dostępu kodu komputera są używane do określania ograniczonych uprawnień na podstawie lokalizacji arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mają najbardziej ograniczone uprawnienia, a arkusze stylów skopiowane na dysk twardy są uruchamiane z pełnym zaufaniem.

- Klasa <xref:System.Xml.Xsl.XslCompiledTransform> jest używana do kompilowania XSLT do języka pośredniego firmy Microsoft w celu zwiększenia wydajności podczas wykonywania.

- Schematy wskazujące lokalizację zewnętrzną w pliku wykazu są automatycznie pobierane po pierwszym załadowaniu edytora XML. Klasa <xref:System.Xml.Schema.XmlSchemaSet> jest używana do kompilowania schematów. Plik wykazu, który jest dostarczany z edytorem XML, nie zawiera linków do żadnych zewnętrznych schematów. Użytkownik musi jawnie dodać odwołanie do zewnętrznego schematu, zanim Edytor XML pobierze plik schematu. Pobieranie HTTP można wyłączyć za pomocą strony **Opcje narzędzi dodatkowych** dla edytora XML.

- Edytor XML używa klas <xref:System.Net> do pobierania schematów

## <a name="xslt-debugger"></a>Debuger XSLT
 Debuger XSLT wykorzystuje zarządzane aparaty debugowania programu Visual Studio i klasy z przestrzeni nazw <xref:System.Xml> i <xref:System.Xml.Xsl>.

- Debuger XSLT uruchamia każdą transformację XSLT w domenie aplikacji w trybie piaskownicy. Zasady zabezpieczeń dostępu kodu komputera są używane do określania ograniczonych uprawnień na podstawie lokalizacji arkusza stylów XSLT. Na przykład arkusze stylów z lokalizacji internetowej mają najbardziej ograniczone uprawnienia, a arkusze stylów skopiowane na dysk twardy są uruchamiane z pełnym zaufaniem.

- Arkusz stylów XSLT jest kompilowany przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.

- Ewaluatora wyrażeń XSLT jest ładowany przez zarządzany aparat debugowania. Zarządzany aparat debugowania zakłada, że cały kod jest uruchamiany z komputera lokalnego użytkownika. W związku z tym Klasa <xref:System.Xml.Xsl.XslCompiledTransform> pobiera plik XSLT na komputer lokalny użytkownika. Możliwe, że może wystąpić podniesienie uprawnień w wykonywaniu, przez wykonanie wszystkich transformacji XSLT w nowej domenie aplikacji z ograniczonymi uprawnieniami

## <a name="see-also"></a>Zobacz też
 [Domeny aplikacji](https://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)
