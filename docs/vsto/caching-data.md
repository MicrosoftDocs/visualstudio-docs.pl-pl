---
title: Dane w pamięci podręcznej
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b46fa8b0138eff03757a7bd7828053cee039090f
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248127"
---
# <a name="cache-data"></a>Dane w pamięci podręcznej
  Może buforować obiekty danych w dostosowaniu na poziomie dokumentu, dzięki czemu dane są dostępne w trybie offline lub bez konieczności otwierania programu Microsoft Office Word lub Microsoft Office Excel. Buforowanie obiektu, obiekt musi mieć typ danych, który spełnia określone wymagania. Wiele standardowe typy danych w programie .NET Framework spełniają te wymagania, w tym <xref:System.String>, <xref:System.Data.DataSet>, i <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Istnieją dwa sposoby, aby dodać obiekt do pamięci podręcznej danych:  
  
- Aby dodać obiekt do pamięci podręcznej danych, podczas kompilowania rozwiązania, należy zastosować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu deklaracja obiektu. Aby uzyskać więcej informacji, zobacz [jak: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
- Aby programowo dodać obiekt do pamięci podręcznej danych w czasie wykonywania, należy użyć `StartCaching` metoda hosta elementów, takich jak `ThisDocument` lub `ThisWorkbook` klasy. Aby uzyskać więcej informacji, zobacz [jak: Programowe buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
  Po dodaniu obiektu do pamięci podręcznej danych można uzyskać dostęp i modyfikować dane w pamięci podręcznej bez konieczności uruchamiania programu Word lub Excel. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Wymagania dla obiektów danych w pamięci podręcznej  
 Buforowanie obiektu danych w swoim rozwiązaniu, obiekt musi spełniać następujące wymagania:  
  
- Być pole publiczne odczytu/zapisu lub właściwości elementu hosta, taką jak `ThisDocument` lub `ThisWorkbook` klasy.  
  
- Nie jest indeksatora lub innych właściwości sparametryzowane.  
  
  Ponadto, obiekt danych musi być możliwy do serializacji, <xref:System.Xml.Serialization.XmlSerializer> klasy, co oznacza, że typ obiektu musi mieć następującą charakterystykę:  
  
- Być typem publicznym.  
  
- Ma on publicznego konstruktora bez parametrów.  
  
- Nie można wykonać kod wymagający uprawnień zabezpieczeń.  
  
- Udostępnianie tylko odczyt/zapis właściwości publiczne (inne właściwości zostaną zignorowane).  
  
- Nie należy uwidaczniać Wielowymiarowe tablice (tablice zagnieżdżone są akceptowane).  
  
- Zwraca interfejsy z właściwości i pola.  
  
- Implementuje <xref:System.Collections.IDictionary> Jeśli kolekcji.  
  
  Gdy buforowanie obiektu danych [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializuje obiekt do ciągu XML, która jest przechowywana w *niestandardowym elementem XML* w dokumencie. Aby uzyskać więcej informacji, zobacz [przegląd części niestandardowy plik XML](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Limity rozmiaru danych w pamięci podręcznej  
 Istnieją pewne ograniczenia łącznej ilości danych, które można dodać do pamięci podręcznej danych w dokumencie, a rozmiar dowolnego pojedynczego obiektu w pamięci podręcznej danych. Po przekroczeniu limitów, aplikacja może zostać nieoczekiwanie zamknięta, gdy dane są zapisywane w pamięci podręcznej danych.  
  
 Aby uniknąć tych ograniczeń, należy przestrzegać następujących wytycznych:  
  
- Nie należy dodawać dowolnego obiektu, które są większe niż 10 MB pamięci podręcznej danych.  
  
- Nie należy dodawać więcej niż 100 MB łączna ilość danych do pamięci podręcznej danych w jednym dokumencie.  
  
  Są to przybliżone wartości. Dokładne ograniczenia zależą od kilku czynników, w tym dostępnej pamięci RAM i liczbę uruchomionych procesów.  
  
## <a name="control-the-behavior-of-cached-objects"></a>Sterowanie zachowaniem obiektów w pamięci podręcznej  
 Aby uzyskać większą kontrolę nad zachowaniem obiektu w pamięci podręcznej, można zaimplementować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfejsu na typ obiektu w pamięci podręcznej. Na przykład można zaimplementować ten interfejs, jeśli chcesz kontrolować, jak użytkownik jest powiadamiany po zmianie obiektu. Aby uzyskać przykłady kodu, które pokazują, jak zaimplementować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, zobacz `ControlCollection` klasy w dynamicznych przykładowe kontrolki programu Excel i Word dynamiczne formanty przykładu w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Utrwalanie zmian w dane w pamięci podręcznej w dokumentach zabezpieczonych hasłem  
 Jeśli użytkownik buforowania obiektów danych w dokumencie, który jest chroniony hasłem, zmiany w buforowanych danych nie są zapisywane. Aby zapisać zmiany na dane w pamięci podręcznej, zastępowanie dwie metody. Zastąpienie tych metod umożliwiających tymczasowe usunięcie ochrony, gdy dokument zostanie zapisany, a następnie ponownie Zastosuj ochronę po zapisu operacja została zakończona.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Buforowanie danych w dokumentach zabezpieczonych hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Zapobieganie utracie danych podczas dodawania wartości null do pamięci podręcznej danych  
 Podczas dodawania obiektów do buforowania danych, wszystkie obiekty w pamięci podręcznej musi zostać zainicjowany do innej niż**null** wartość przed dokument zostanie zapisany i zamknięte. Jeśli ma dowolnego obiektu w pamięci podręcznej **null** wartości, gdy dokument zostanie zapisany i zamknięte, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] spowoduje automatyczne usunięcie wszystkich buforowanych obiektów z pamięci podręcznej danych.  
  
 W przypadku dodania obiektu z **null** wartość do pamięci podręcznej danych przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu w czasie projektowania, można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> obiekty klasy, aby zainicjować dane w pamięci podręcznej, przed otwarciem dokumentu. Jest to przydatne, jeśli chcesz zainicjować pamięci podręcznej danych na serwerze bez programu Word lub Excel zainstalowany, przed otwarciem dokumentu przez użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Instrukcje: Programowe buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Instrukcje: Dane w pamięci podręcznej w dokumentach zabezpieczonych hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Wskazówki: Tworzenie relacji wzorzec szczegół za pomocą pamięci podręcznej zestawu danych](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  