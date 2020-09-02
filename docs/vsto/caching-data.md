---
title: Dane pamięci podręcznej
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e0f6d7fcf9920ddb8861712b7c5f8bf04506fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62939418"
---
# <a name="cache-data"></a>Dane pamięci podręcznej
  Można buforować obiekty danych w dostosowaniu na poziomie dokumentu, aby można było uzyskać dostęp do danych w trybie offline lub bez otwierania Microsoft Office Word lub Microsoft Office Excel. Aby można było buforować obiekt, obiekt musi mieć typ danych spełniający określone wymagania. Wiele typowych typów danych w .NET Framework spełnia te wymagania, w tym <xref:System.String> , <xref:System.Data.DataSet> i <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Istnieją dwa sposoby dodawania obiektu do pamięci podręcznej danych:

- Aby dodać obiekt do pamięci podręcznej danych podczas kompilowania rozwiązania, Zastosuj <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybut do deklaracji obiektu. Aby uzyskać więcej informacji, zobacz [jak: dane pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Aby programowo dodać obiekt do pamięci podręcznej danych w czasie wykonywania, użyj `StartCaching` metody elementu hosta, na przykład `ThisDocument` `ThisWorkbook` klasy lub. Aby uzyskać więcej informacji, zobacz [How to: programowe buforowanie źródła danych w dokumencie pakietu Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Po dodaniu obiektu do pamięci podręcznej danych można uzyskać dostęp do buforowanych danych i modyfikować je bez uruchamiania programu Word lub Excel. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Wymagania dotyczące obiektów danych do zbuforowania
 Aby buforować obiekt danych w rozwiązaniu, obiekt musi spełniać następujące wymagania:

- Być polem publicznym odczytu/zapisu lub właściwością elementu hosta, na przykład `ThisDocument` `ThisWorkbook` klasą lub.

- Nie być indeksatorem ani inną właściwością sparametryzowanej.

  Ponadto obiekt danych musi być możliwy do serializacji przez <xref:System.Xml.Serialization.XmlSerializer> klasę, co oznacza, że typ obiektu musi mieć następującą charakterystykę:

- Być typem publicznym.

- Mieć Konstruktor publiczny bez parametrów.

- Nie wykonuj kodu, który wymaga dodatkowych uprawnień zabezpieczeń.

- Uwidaczniaj tylko właściwości publiczne odczytu/zapisu (inne właściwości zostaną zignorowane).

- Nie uwidaczniaj wielowymiarowych tablic (zaakceptowane są zagnieżdżone tablice).

- Nie zwracają interfejsów z właściwości i pól.

- Nie Wdrażaj <xref:System.Collections.IDictionary> , jeśli kolekcja.

  W pamięci podręcznej obiektu danych, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializacja obiektu do ciągu XML, który jest przechowywany w *NIESTANDARDOWEJ części XML* w dokumencie. Aby uzyskać więcej informacji, zobacz temat [niestandardowe składniki XML — Omówienie](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Limity rozmiaru danych w pamięci podręcznej
 Istnieją pewne ograniczenia dotyczące całkowitej ilości danych, które można dodać do pamięci podręcznej danych w dokumencie, oraz do rozmiaru każdego pojedynczego obiektu w pamięci podręcznej danych. W przypadku przekroczenia tych limitów aplikacja może zostać nieoczekiwanie ZAMKNIĘTA, gdy dane są zapisywane w pamięci podręcznej danych.

 Aby uniknąć tych limitów, postępuj zgodnie z następującymi wskazówkami:

- Nie dodawaj żadnego obiektu większego niż 10 MB do pamięci podręcznej danych.

- Nie należy dodawać więcej niż 100 MB całkowitej ilości danych do pamięci podręcznej danych w jednym dokumencie.

  Są to przybliżone wartości. Dokładne limity są zależne od kilku czynników, w tym dostępnej pamięci RAM i liczby uruchomionych procesów.

## <a name="control-the-behavior-of-cached-objects"></a>Sterowanie zachowaniem buforowanych obiektów
 Aby uzyskać większą kontrolę nad zachowaniem buforowanych obiektów, można zaimplementować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfejs na typ obiektu w pamięci podręcznej. Można na przykład zaimplementować ten interfejs, jeśli chcesz kontrolować sposób powiadamiania użytkownika o zmianie obiektu. Aby zapoznać się z przykładami kodu, które demonstrują sposób implementacji <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> , zobacz klasę w przykładowym formancie `ControlCollection` dynamicznym programu Excel i przykładowymi kontrolkami dynamicznymi programu Word w podręczniku [i przewodnikach tworzenia pakietu Office](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Utrwalaj zmiany danych w pamięci podręcznej w dokumentach chronionych hasłem
 W przypadku buforowania obiektów danych w dokumencie chronionym hasłem zmiany w pamięci podręcznej nie są zapisywane. Zmiany w buforowanych danych można zapisać przez zastępowanie dwóch metod. Przesłoń te metody, aby tymczasowo usunąć ochronę podczas zapisywania dokumentu, a następnie ponownie Zastosuj ochronę po zakończeniu operacji zapisywania.

 Aby uzyskać więcej informacji, zobacz [jak: dane w pamięci podręcznej w dokumencie chronionym hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Zapobiegaj utracie danych podczas dodawania wartości null do pamięci podręcznej danych
 Po dodaniu obiektów do pamięci podręcznej danych, wszystkie obiekty w pamięci podręcznej muszą zostać zainicjowane do wartości innej niż**null** przed zapisaniem i zamknięciem dokumentu. Jeśli dowolny buforowany obiekt ma wartość **null** , gdy dokument jest zapisywany i zamknięty, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] program automatycznie usunie wszystkie obiekty z pamięci podręcznej.

 Jeśli dodasz obiekt z wartością **null** do pamięci podręcznej danych przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu w czasie projektowania, możesz użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy, aby zainicjować buforowane obiekty danych przed otwarciem dokumentu. Jest to przydatne, jeśli chcesz zainicjować dane z pamięci podręcznej na serwerze bez zainstalowanego programu Word lub Excel, zanim dokument zostanie otwarty przez użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dane z pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Instrukcje: programowane buforowanie źródła danych w dokumencie pakietu Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Instrukcje: buforowanie danych w dokumencie chronionym hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Wskazówki: Tworzenie relacji głównej szczegółów przy użyciu buforowanego zestawu danych](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
