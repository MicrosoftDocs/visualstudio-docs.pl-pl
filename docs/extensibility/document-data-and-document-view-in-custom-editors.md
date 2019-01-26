---
title: Dane dokumentu i dokument widok w edytorach niestandardowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f2deb04f14af93846b0b5a9e13dca14eb5ed710
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020155"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dane dokumentu i Widok dokumentu w edytorach niestandardowych
Niestandardowy edytor, który składa się z dwóch części: obiekt danych dokumentu i obiekt widoku dokumentu. Jak sugerują nazwy dokumentu obiekt danych reprezentuje dane tekstowe, które mają być wyświetlane. Podobnie obiekt widoku dokumentu (lub "view") przedstawia jednego lub kilku okien, w której chcesz wyświetlić obiekt danych dokumentu.  
  
## <a name="document-data-object"></a>Obiekt danych dokumentu  
 Obiekt danych dokumentu jest reprezentacja danych tekstu w buforze tekstu. Jest obiektu COM, który przechowuje tekstu dokumentu i inne informacje. Obiekt danych dokumentu również obsługuje trwałość dokumentu i umożliwia jego danych z wielu widoków. Aby uzyskać więcej informacji, zobacz artykuł  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> i [dokumentu Windows](../extensibility/internals/document-windows.md).  
  
 Niestandardowych edytorów i projektantów, można zdecydować się na użycie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu lub własne niestandardowe buforu. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> następuje uproszczony model osadzania dla standardowego edytora, obsługuje wielu widoków i zapewnia interfejsy zdarzeń, które są używane do zarządzania wielu widoków.  
  
## <a name="document-view-object"></a>Obiekt widoku dokumentu  
 Okno które wyświetla kod i inne teksty jest znany jako dokument widok lub widok. Podczas tworzenia edytora można albo pojedynczy widok, w którym tekst jest wyświetlany w jednym oknie. Lub możesz wybrać wiele widok, w którym tekst jest wyświetlany w więcej niż jedno okno. Wybór zależy od aplikacji. Na przykład edytowanie side-by-side, należy wybrać wiele widoku. Każdy widok jest skojarzony z wpisem w zintegrowanym środowisku programistycznym firmy (IDE) uruchamianie tabeli dokumentu (Normalizacją). Widok systemu windows należy do projektu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu.  
  
 Jeśli Edytor obsługuje wielu widoków dokumentu obiektu danych, dokumentów, danych i obiektów widoku dokumentu musi być oddzielne. W przeciwnym razie one mogą być grupowane razem. Aby uzyskać więcej informacji, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
 IDE powiadamia widoków o zdarzeniach (na przykład, gdy rozwiązanie zawierające dokumentu jest zamknięty), przez dopasowanie identyfikatora elementu (identyfikator elementu) dla każdej pozycji w uruchomionej tabeli dokumentu. Aby uzyskać więcej informacji na temat tego, zobacz [uruchamianie tabeli dokumentu](../extensibility/internals/running-document-table.md).  
  
 Dostępne są dwie opcje dotyczące tworzenia widoku niestandardowego edytora. Jeden jest modelu aktywacji w miejscu, gdzie widoku znajduje się w oknie za pomocą formantu ActiveX lub obiektu danych dokumentu. Drugim jest uproszczony model osadzania, gdy widok jest hostowana przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> jest zaimplementowana w oknie poleceń. Aby uzyskać informacje na temat modelu aktywacji w miejscu, zobacz [Aktywacja w miejscu](../extensibility/in-place-activation.md). Aby uzyskać informacji na temat uproszczony model osadzania, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Uproszczone osadzanie](../extensibility/simplified-embedding.md)   
 [Instrukcje: Dołączanie widoków do danych dokumentu](../extensibility/how-to-attach-views-to-document-data.md)   
 [Zarządzanie właścicielem blokady dokumentu](../extensibility/document-lock-holder-management.md)   
 [Widoki jedną i wieloma kartami](../extensibility/single-and-multi-tab-views.md)   
 [Zapisywanie standardowego dokumentu](../extensibility/internals/saving-a-standard-document.md)   
 [Trwałość i uruchamianie tabeli dokumentu](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Określić, które edytora otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fabryki edytora](../extensibility/editor-factories.md)