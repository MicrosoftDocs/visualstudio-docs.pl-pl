---
title: Dane w pamięci podręcznej w dostosowaniu na poziomie dokumentu
description: Dowiedz się, w jaki sposób program Visual Studio oddziela dane z widoku w dostosowaniach na poziomie dokumentu, włączając dane do osadzenia jako pamięć podręczną danych.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be4229c179ec6c5640ab612d28991fe476363a53
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847900"
---
# <a name="cached-data-in-document-level-customizations"></a>Dane w pamięci podręcznej w dostosowaniu na poziomie dokumentu
  Podstawowym celem dostosowań na poziomie dokumentu jest oddzielenie danych z widoku w dokumentach pakietu Office. Dane odnoszą się do informacji przechowywanych w dokumencie, w tym liczb i tekstu. Widok odnosi się do interfejsu użytkownika i modelu obiektów Microsoft Office Word i Microsoft Office Excel.

 Program Visual Studio oddziela dane z widoku w dostosowaniach na poziomie dokumentu przez włączenie danych do osadzenia jako *wyspa danych*, nazywanej również *pamięcią podręczną danych*. Możesz odczytywać lub modyfikować dane bezpośrednio bez uruchamiania programu Word lub Excel. Jest to przydatne w przypadku konieczności modyfikacji danych w dokumentach na serwerze, na którym nie zainstalowano Microsoft Office. Programy Word i Excel są przeznaczone do użycia w środowiskach klienckich. nie są one przeznaczone do uruchamiania na serwerze.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Aby uzyskać więcej informacji na temat dostosowań na poziomie dokumentu, zobacz temat [programowanie rozwiązań pakietu Office omówienie &#40;narzędzia VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) i [architektury dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Omówienie modelu programowania danych w pamięci podręcznej
 Wyspa danych może zawierać dowolne obiekty w rozwiązaniu, które spełniają określone wymagania. Te obiekty obejmują <xref:System.Data.DataSet> obiekty, <xref:System.Data.DataTable> obiekty i inne inne obiekty, które mogą być serializowane przez <xref:System.Xml.Serialization.XmlSerializer> klasę. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).

 Aby zapewnić widok danych w pamięci podręcznej, można powiązać kontrolki Windows Forms i *kontrolki hosta* w dokumencie z obiektami na Wyspach danych. Powiązanie danych między wyspami danych i kontrolkami związanymi z danymi utrzymuje dwie zsynchronizowane. Możesz również dodać kod weryfikacyjny do danych, które są niezależne od kontrolek. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Formanty hosta są rozszerzonymi wersjami obiektów natywnych w modelu obiektów programu Excel i programu Word. W przeciwieństwie do obiektów natywnych, formanty hosta mogą być powiązane bezpośrednio z obiektami danych zarządzanych. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md) oraz [formanty Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Dostęp do danych w pamięci podręcznej na serwerze
 Aby uzyskać dostęp do danych w pamięci podręcznej w dokumencie, można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy. Ta klasa jest częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i może być używana na serwerze bez programu Excel lub Word. Gdy użytkownik otwiera dokument po zmodyfikowaniu danych w pamięci podręcznej, wszystkie kontrolki, które są powiązane z danymi, są automatycznie synchronizowane ze zmianami, a użytkownik otrzymuje zaktualizowane dane. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).

 Program Excel i program Word nie są niezbędne do zapisu danych na serwerze, tylko w celu wyświetlenia ich na kliencie. Programy Excel i Word nie muszą nawet być zainstalowane na serwerze. Zapewnia to lepszą skalowalność i możliwość szybkiego przetwarzania wsadowego dokumentów zawierających Wyspy danych.

## <a name="data-caching-for-offline-use"></a>Buforowanie danych do użycia w trybie offline
 Przechowywanie danych na Wyspach danych umożliwia wykonywanie scenariuszy w trybie offline. Gdy użytkownik otwiera dokument lub żąda dokumentu z serwera, Wyspa danych jest wypełniana najnowszymi danymi. Wyspa danych jest buforowana w dokumencie, a następnie jest dostępna w trybie offline. Użytkownik (i kod) mogą manipulować danymi, nawet jeśli nie jest dostępne żadne połączenie na żywo. Gdy użytkownik ponownie nawiązuje połączenie, zmiany danych mogą zostać przekazane z powrotem do źródła danych serwera.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Porównano dane buforowane i niestandardowe części XML
 Niestandardowe części XML wprowadzono w systemie 2007 Microsoft Office jako sposób przechowywania dowolnych fragmentów kodu XML w dokumencie. Chociaż niestandardowe części XML są przydatne w wielu różnych scenariuszach, co w przypadku pamięci podręcznej, istnieją pewne różnice między wyspami danych i niestandardowymi składnikami XML. Aby uzyskać więcej informacji na temat niestandardowych części XML, zobacz temat [niestandardowe składniki XML — Omówienie](../vsto/custom-xml-parts-overview.md).

 W poniższej tabeli wymieniono niektóre różnice i podobieństwa.

|Pytanie/cecha|Pamięć podręczna danych|Niestandardowe części XML|
|-|----------------|----------------------|
|Które aplikacje pakietu Office mogą z nich korzystać?|Dostosowania na poziomie dokumentu dla następujących aplikacji:<br /><br /> — Excel<br />-Word|Rozwiązania na poziomie dokumentu i aplikacji dla następujących aplikacji:<br /><br /> — Excel<br />— PowerPoint<br />-Word|
|Jakie typy danych można przechowywać?|Dowolny obiekt publiczny w zestawie dostosowań, który spełnia określone wymagania. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).|Dowolne dane XML.|
|Czy można uzyskać dostęp do danych bez uruchamiania Microsoft Office aplikacji?|Tak, za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy dostarczonej przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Tak, przy użyciu klas w <xref:System.IO.Packaging> przestrzeni nazw lub przy użyciu zestawu SDK Open XML format.|

## <a name="see-also"></a>Zobacz także
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
