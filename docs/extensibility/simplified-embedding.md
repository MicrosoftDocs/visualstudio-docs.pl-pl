---
title: Uproszczone osadzanie | Microsoft Docs
description: Zapoznaj się z uproszczonym osadzaniem, które można włączyć w edytorze, gdy jego obiekt widoku dokumentu jest elementem podrzędnym programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99aaf5070646bbbb95c6be98eb8ac2f7a5948ff2
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715278"
---
# <a name="simplified-embedding"></a>Uproszczone osadzanie
Uproszczone osadzanie jest włączane w edytorze, gdy jego obiekt widoku dokumentu jest nadrzędny względem (czyli elementu podrzędnego) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejs jest zaimplementowany do obsługi poleceń okna. Uproszczone edytory osadzania nie mogą hostować aktywnych kontrolek. Obiekty używane do tworzenia edytora z uproszczonym osadzaniem są pokazane na poniższej ilustracji.

 ![Grafika uproszczonego edytora osadzania](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Edytor z uproszczonym osadzaniem

> [!NOTE]
> Obiektów na tej ilustracji tylko `CYourEditorFactory` obiekt jest wymagany do utworzenia standardowego edytora opartego na plikach. Jeśli tworzysz Edytor niestandardowy, nie musisz wdrażać programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , ponieważ twój edytor prawdopodobnie będzie miał własny prywatny mechanizm trwałości. Jednak w przypadku edytorów innych niż niestandardowe należy to zrobić.

 Wszystkie interfejsy zaimplementowane w celu utworzenia edytora z uproszczonym osadzaniem są zawarte w `CYourEditorDocument` obiekcie. Aby jednak obsługiwać wiele widoków danych dokumentu, należy podzielić interfejsy na oddzielne dane i wyświetlić obiekty, jak wskazano w poniższej tabeli.

|Interfejs|Lokalizacja interfejsu|Zastosowanie|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Widok|Zapewnia połączenie z oknem nadrzędnym.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Widok|Obsługuje polecenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Widok|Włącza aktualizacje paska stanu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Widok|Włącza elementy **przybornika** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dane|Wysyła powiadomienia, gdy plik ulegnie zmianie.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dane|Włącza funkcję Zapisz jako dla typu pliku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dane|Włącza trwałość dla dokumentu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dane|Umożliwia pominięcie zdarzeń zmiany plików, takich jak ponowne ładowanie wyzwalania.|
