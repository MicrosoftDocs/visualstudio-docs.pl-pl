---
title: Dane dokumentu i dokument widok w edytorach niestandardowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55f082711de306e9dd22fdf55e769282ad150f17
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755299"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dane dokumentu i widok dokumentu w edytorach niestandardowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niestandardowy edytor, który składa się z dwóch części: obiekt danych dokumentu i obiekt widoku dokumentu. Jak sugerują nazwy dokumentu obiekt danych reprezentuje dane tekstowe, które mają być wyświetlane, a obiekt widoku dokumentu (lub "view") — jednego lub kilku okien, w której chcesz wyświetlić obiekt danych dokumentu.  
  
## <a name="document-data-object"></a>Obiekt danych dokumentu  
 Obiekt danych dokumentu jest reprezentacja danych tekstu w buforze tekstu. Jest obiekt COM, który przechowuje tekstu dokumentu i inne informacje, obsługuje trwałość dokumentu i umożliwia jego danych z wielu widoków. Aby uzyskać więcej informacji, zobacz artykuł  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> i [dokumentu Windows](../extensibility/internals/document-windows.md).  
  
 Niestandardowych edytorów i projektantów, można zdecydować się na użycie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu lub własne niestandardowe buforu. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> następuje uproszczony model osadzania dla standardowego edytora, obsługuje wielu widoków i zapewnia interfejsy zdarzeń, które są używane do zarządzania wielu widoków.  
  
## <a name="document-view-object"></a>Obiekt widoku dokumentu  
 Okno które wyświetla kod i inne teksty jest znany jako dokument widok lub widok. Podczas tworzenia edytora, można wybrać pojedynczy widok, w którym tekst jest wyświetlany w jednym oknie lub wielu widok, w którym tekst jest wyświetlany w więcej niż jedno okno. Wybór zależy od aplikacji. Na przykład edytowanie side-by-side, należy wybrać wiele widoku. Każdy widok jest skojarzony z wpisem w zintegrowanym środowisku programistycznym firmy (IDE) uruchamianie tabeli dokumentu (Normalizacją). Widok systemu windows należy do projektu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu.  
  
 Jeśli Edytor obsługuje wielu widoków dokumentu obiektu danych, dokumentów, danych i obiektów widoku dokumentu musi być oddzielne. W przeciwnym razie one mogą być grupowane razem. Aby uzyskać więcej informacji, zobacz [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
 IDE powiadamia widoków o zdarzeniach (na przykład, gdy rozwiązanie zawierające dokumentu jest zamknięty), przez dopasowanie identyfikatora elementu (identyfikator elementu) dla każdej pozycji w uruchomionej tabeli dokumentu. Aby uzyskać więcej informacji na temat tego, zobacz [uruchamianie tabeli dokumentu](../extensibility/internals/running-document-table.md).  
  
 Dostępne są dwie opcje dotyczące tworzenia widoku niestandardowego edytora. Jeden jest modelu aktywacji w miejscu, gdzie widoku znajduje się w oknie za pomocą formantu ActiveX lub obiektu danych dokumentu. Drugim jest uproszczony model osadzania, gdy widok jest hostowana przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> jest zaimplementowana w oknie poleceń. Aby uzyskać informacje na temat modelu aktywacji w miejscu, zobacz [aktywacji w miejscu](../misc/in-place-activation.md). Aby uzyskać informacji na temat uproszczony model osadzania, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Uproszczone osadzanie](../extensibility/simplified-embedding.md)   
 [Porady: dołączanie widoków do danych dokumentów](../extensibility/how-to-attach-views-to-document-data.md)   
 [Zarządzanie właścicielem blokady dokumentu](../extensibility/document-lock-holder-management.md)   
 [Widoki jedną i wieloma kartami](../extensibility/single-and-multi-tab-views.md)   
 [Zapisywanie standardowego dokumentu](../extensibility/internals/saving-a-standard-document.md)   
 [Trwałość i uruchamianie tabeli dokumentów](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Określanie który Edytor służy do otwierania pliku w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fabryki edytorów](../extensibility/editor-factories.md)

