---
title: Dane w pamięci podręcznej dostosowywane na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: c17c24dda11ea210c190a31197b783036357f2de
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248299"
---
# <a name="cached-data-in-document-level-customizations"></a>Dane w pamięci podręcznej dostosowywane na poziomie dokumentu
  Podstawowym celem dostosowania poziomu dokumentu jest oddzielenie danych z widoku w dokumentach pakietu Office. Danych odnosi się do informacji, które są przechowywane w dokumencie, w tym liczby i tekst. Widok odwołuje się do interfejsu użytkownika i modelu obiektów programu Microsoft Office Word i Microsoft Office Excel.  
  
 Program Visual Studio oddziela dane z widoku w dostosowaniach na poziomie dokumentu, należy włączyć danych w celu osadzenia jako *Wyspy danych*, nazywane również *pamięci podręcznej danych*. Ty możesz odczytywać i modyfikować dane bezpośrednio bez konieczności uruchamiania programu Word lub Excel. Jest to przydatne, jeśli zachodzi konieczność zmiany danych w dokumentach na serwerze, na którym nie ma zainstalowany w Microsoft Office. Word i Excel, które są przeznaczone do użytku w środowiskach klienckich; nie są przeznaczone do uruchamiania na serwerze.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aby uzyskać więcej informacji na temat dostosowywania poziomie dokumentu, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Informacje o modelu programowania dane w pamięci podręcznej  
 Wyspy danych może zawierać dowolny obiekt w Twoim rozwiązaniu, które spełnia określone wymagania. Te obiekty obejmują <xref:System.Data.DataSet> obiektów <xref:System.Data.DataTable> obiektów i inny obiekt, który może być serializowany przez <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).  
  
 Aby zapewnić widoku dane w pamięci podręcznej, można powiązać kontrolek formularzy Windows Forms i *hostowania kontrolek* dokumentu do obiektów w Wyspy danych. Powiązanie danych między Wyspy danych i kontrolek powiązanych z danymi przechowuje dwie zsynchronizowane. Można również dodać kod sprawdzania poprawności, danych, który jest niezależny od kontrolek. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Formanty hosta zostały rozszerzone wersji obiektów natywnych w modelach obiektów programu Excel i Word. W przeciwieństwie do natywnych obiektów formanty hosta może być powiązana bezpośrednio do obiektów zarządzanych danych. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md) i [kontrolek formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Dostęp do pamięci podręcznej danych na serwerze  
 Aby uzyskać dostęp do danych z pamięci podręcznej dokumentu, można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy. Ta klasa jest częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], i mogą być używane na serwerze bez uruchomionego programu Excel lub Word. Gdy użytkownik otwiera dokument po modyfikować dane w pamięci podręcznej, formanty, które są powiązane z danymi są automatycznie synchronizowane na zmiany, a użytkownik zobaczy ze zaktualizowanymi danymi. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Program Excel i Word nie są potrzebne do zapisu danych na serwerze, tylko po to, aby wyświetlić go na komputerze klienckim. Program Excel i Word nie musi nawet można zainstalować na serwerze. Dzięki temu zwiększona skalowalność i możliwość wykonywania przetwarzania wsadowego szybkie dokumentów zawierających Wyspy danych.  
  
## <a name="data-caching-for-offline-use"></a>Buforowanie w trybie offline danych  
 Przechowywanie danych w Wyspy danych pozwala scenariusze w trybie offline. Gdy użytkownik najpierw otwiera dokument lub żądań dokumentu z serwera, Wyspy danych jest wypełniony przy użyciu najnowszych danych. Wyspy danych są buforowane w dokumencie i będzie dostępny w trybie offline. Użytkownik (i kodu) można manipulować danymi, nawet jeśli nie połączenie na żywo jest dostępna. Gdy użytkownik połączy się ponownie, zmiany w danych można propagowany z powrotem do źródła danych serwera.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Dane w pamięci podręcznej i niestandardowe elementy XML w porównaniu  
 Niestandardowe elementy XML zostały wprowadzone w programie Microsoft Office system 2007 jako sposób na przechowywanie dowolnych fragmentów kodu XML w dokumencie. Mimo że niestandardowe elementy XML są przydatne w wielu z tych samych scenariuszy co pamięć podręczna danych, istnieją pewne różnice między Wyspy danych i niestandardowe elementy XML. Aby uzyskać więcej informacji na temat niestandardowych części XML, zobacz [przegląd części niestandardowy kod XML](../vsto/custom-xml-parts-overview.md).  
  
 Poniższa lista zawiera niektóre różnice i podobieństwa.  
  
||Pamięć podręczna danych|Niestandardowe elementy XML|  
|-|----------------|----------------------|  
|Które aplikacje pakietu Office można użyć tych?|Dostosowania poziomu dokumentu dla następujących aplikacji:<br /><br /> — Excel<br />-Programu Word|Rozwiązania dokumentu i na poziomie aplikacji dla następujących aplikacji:<br /><br /> — Excel<br />— PowerPoint<br />-Programu Word|  
|Jakie typy danych można przechowywać?|Dowolnego obiektu publicznego w zestawie swoje dostosowania, który spełnia określone wymagania. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).|Wszelkie dane XML.|  
|Czy masz dostęp do danych bez uruchamiania aplikacji Microsoft Office?|Tak, za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> dostarczane przez klasy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Tak, korzystając z klas w <xref:System.IO.Packaging> przestrzeni nazw, lub za pomocą Open XML Format SDK.|  
  
## <a name="see-also"></a>Zobacz także  
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  