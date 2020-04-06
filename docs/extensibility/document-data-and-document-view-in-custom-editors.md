---
title: Dane dokumentu i widok dokumentu w edytorach niestandardowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712145"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Wyświetlanie danych i dokumentów w edytorach niestandardowych
Edytor niestandardowy składa się z dwóch części: obiektu danych dokumentu i obiektu widoku dokumentu. Jak sugerują nazwy, obiekt danych dokumentu reprezentuje dane tekstowe, które mają być wyświetlane. Podobnie obiekt widoku dokumentu (lub "widok") reprezentuje jedno lub więcej okien, w których ma być wyświetlany obiekt danych dokumentu.

## <a name="document-data-object"></a>Obiekt danych dokumentu
 Obiekt danych dokumentu jest reprezentacją danych tekstu w buforze tekstowym. Jest to obiekt COM, który przechowuje tekst dokumentu i inne informacje. Obiekt danych dokumentu obsługuje również trwałość dokumentu i umożliwia wiele widoków jego danych. Aby uzyskać więcej informacji, zobacz

 <xref:EnvDTE80.Window2.DocumentData%2A>i [Dokument Systemu Windows](../extensibility/internals/document-windows.md).

 Edytorzy i projektanci niestandardowi <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> mogą zdecydować się na użycie obiektu lub własnego buforu niestandardowego. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>podąża za uproszczonym modelem osadzania dla standardowego edytora, obsługuje wiele widoków i udostępnia interfejsy zdarzeń, które są używane do zarządzania wieloma widokami.

## <a name="document-view-object"></a>Obiekt widoku dokumentu
 Okno, w które wyświetla kod i inny tekst jest znany jako widok dokumentu lub widok. Podczas tworzenia edytora można wybrać pojedynczy widok, w którym tekst jest wyświetlany w jednym oknie. Można też wybrać widok wielokrotny, w którym tekst jest wyświetlany w więcej niż jednym oknie. Wybór zależy od aplikacji. Na przykład, jeśli potrzebujesz edycji obok siebie, należy wybrać widok wielokrotny. Każdy widok jest skojarzony z wpisem w tabeli dokumentów (IDE) (IDE) (Integrated Development Environment) z systemem (RDT). Okna widoku należą do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu lub obiektu.

 Jeśli edytor obsługuje wiele widoków obiektu danych dokumentu, dane dokumentu i obiekty widoku dokumentu muszą być oddzielne. W przeciwnym razie mogą być zgrupowane razem. Aby uzyskać więcej informacji, zobacz [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).

 IDE powiadamia widoki o zdarzeniach (na przykład, gdy rozwiązanie zawierające dokument jest zamknięty) przez dopasowanie identyfikatora elementu (ItemID) dla każdego wpisu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji na ten temat, zobacz [Uruchamianie tabeli dokumentów](../extensibility/internals/running-document-table.md).

 Istnieją dwie opcje tworzenia widoku dla edytora niestandardowego. Jednym z nich jest model aktywacji w miejscu, gdzie widok jest obsługiwany w oknie przy użyciu formantu ActiveX lub obiektu danych dokumentu. Drugi to uproszczony model osadzania, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> widok jest obsługiwany przez i jest implementowany do obsługi poleceń okna. Aby uzyskać informacje o modelu aktywacji w miejscu, zobacz [Aktywacja w miejscu](/visualstudio/misc/in-place-activation?view=vs-2015). Aby uzyskać informacje na temat uproszczonego modelu osadzania, zobacz [Uproszczone osadzanie](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Zobacz też

- [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)
- [Uproszczone osadzanie](../extensibility/simplified-embedding.md)
- [Jak: Dołączanie widoków do danych dokumentu](../extensibility/how-to-attach-views-to-document-data.md)
- [Zarządzanie posiadaczami blokady dokumentów](../extensibility/document-lock-holder-management.md)
- [Widoki jedno- i wieloksowe](../extensibility/single-and-multi-tab-views.md)
- [Zapisywanie standardowego dokumentu](../extensibility/internals/saving-a-standard-document.md)
- [Trwałość i bieżąca tabela dokumentów](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Określanie, który edytor otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
