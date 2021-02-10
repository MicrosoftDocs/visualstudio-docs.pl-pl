---
title: Dane dokumentu i widok dokumentu w edytorach niestandardowych | Microsoft Docs
description: Dowiedz się więcej o składnikach niestandardowego edytora, które są obiektem danych dokumentu i obiektem widoku dokumentu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89f2903b2ec1308692f629c40af06f89706a427b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968297"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dane dokumentu i widok dokumentu w edytorach niestandardowych
Edytor niestandardowy składa się z dwóch części: obiektu danych dokumentu i obiektu widoku dokumentu. Jak nazwy sugerują, obiekt danych dokumentu reprezentuje dane tekstowe do wyświetlenia. Analogicznie, obiekt widoku dokumentu (lub "widok") reprezentuje jedno lub więcej okien, w których ma zostać wyświetlony obiekt danych dokumentu.

## <a name="document-data-object"></a>Obiekt danych dokumentu
 Obiekt danych dokumentu to reprezentacja tekstu w buforze tekstu. Jest to obiekt COM, który przechowuje tekst dokumentu i inne informacje. Obiekt danych dokumentu obsługuje również trwałość dokumentu i umożliwia korzystanie z wielu widoków danych. Aby uzyskać więcej informacji, zobacz

 <xref:EnvDTE80.Window2.DocumentData%2A> i [okna dokumentów](../extensibility/internals/document-windows.md).

 Edytory niestandardowe i projektanci mogą zrezygnować z użycia <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu lub własnego bufora niestandardowego. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> zgodnie z uproszczonym modelem osadzania dla edytora standardowego program obsługuje wiele widoków i udostępnia interfejsy zdarzeń, które są używane do zarządzania wieloma widokami.

## <a name="document-view-object"></a>Obiekt widoku dokumentu
 Okno, które wyświetla kod i inny tekst jest znany jako widok dokumentu lub widok. Podczas tworzenia edytora można wybrać pojedynczy widok, w którym tekst jest wyświetlany w jednym oknie. Można też wybrać wiele widoków, w których tekst jest wyświetlany w więcej niż jednym oknie. Wybór zależy od aplikacji. Na przykład jeśli potrzebujesz edycji równoczesnej, wybierz wiele widoków. Każdy widok jest skojarzony z wpisem w zintegrowanym środowisku programistycznym (IDE) z uruchomioną tabelą dokumentu (RDT). Widok okna należy do projektu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu.

 Jeśli Edytor obsługuje wiele widoków obiektu danych dokumentu, to dane dokumentu i obiekty widoku dokumentu muszą być oddzielone. W przeciwnym razie mogą być zgrupowane razem. Aby uzyskać więcej informacji, zobacz [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).

 IDE powiadamia widoki o zdarzeniach (na przykład gdy rozwiązanie zawierające dokument jest zamknięte) przez dopasowanie identyfikatora elementu (ItemID) dla każdego wpisu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji na ten temat, zobacz [Uruchamianie tabeli dokumentów](../extensibility/internals/running-document-table.md).

 Dostępne są dwie opcje tworzenia widoku dla niestandardowego edytora. Jednym z nich jest model aktywacji w miejscu, w którym widok jest hostowany w oknie przy użyciu kontrolki ActiveX lub obiektu danych dokumentu. Drugim jest uproszczony model osadzania, w którym widok jest hostowany [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> jest zaimplementowany do obsługi poleceń okna. Aby uzyskać informacje o modelu aktywacji w miejscu, zobacz [Aktywacja w miejscu](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Aby uzyskać informacje o uproszczonym modelu osadzania, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Zobacz też

- [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md)
- [Uproszczone osadzanie](../extensibility/simplified-embedding.md)
- [Instrukcje: dołączanie widoków do danych dokumentu](../extensibility/how-to-attach-views-to-document-data.md)
- [Zarządzanie posiadaczem blokady dokumentu](../extensibility/document-lock-holder-management.md)
- [Pojedyncze i wielotabulacjowe widoki](../extensibility/single-and-multi-tab-views.md)
- [Zapisz dokument standardowy](../extensibility/internals/saving-a-standard-document.md)
- [Trwałość i uruchomiona tabela dokumentów](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Określ, który Edytor otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)