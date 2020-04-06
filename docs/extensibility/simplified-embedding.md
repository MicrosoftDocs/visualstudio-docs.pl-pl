---
title: Uproszczone osadzanie | Dokumenty firmy Microsoft
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
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700070"
---
# <a name="simplified-embedding"></a>Uproszczone osadzanie
Uproszczone osadzanie jest włączone w edytorze, gdy jego obiekt widoku dokumentu jest [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nadrzędny <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> do (czyli wykonane element podrzędny) i interfejs jest zaimplementowany do obsługi jego polecenia okna. Uproszczone edytory osadzania nie mogą obsługiwać aktywnych formantów. Obiekty użyte do utworzenia edytora z uproszczonym osadzaniem są pokazane na poniższej ilustracji.

 ![Uproszczona grafika edytora osadzania](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Edytor z uproszczonym osadzaniem

> [!NOTE]
> Z obiektów na tej ilustracji tylko `CYourEditorFactory` obiekt jest wymagany do utworzenia standardowego edytora opartego na plikach. Jeśli tworzysz edytor niestandardowy, nie są wymagane <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>do zaimplementowania, ponieważ edytor prawdopodobnie będzie miał swój własny mechanizm trwałości prywatnej. Jednak w przypadku edytorów innych niż niestandardowe należy to zrobić.

 Wszystkie interfejsy zaimplementowane w celu utworzenia edytora z uproszczonym osadzaniem są zawarte w `CYourEditorDocument` obiekcie. Jednak do obsługi wielu widoków danych dokumentu, podzielić interfejsy na oddzielne dane i wyświetlić obiekty, jak wskazano w poniższej tabeli.

|Interface|Lokalizacja interfejsu|Użycie|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Widok|Zapewnia połączenie z oknem nadrzędnym.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Widok|Obsługuje polecenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Widok|Włącza aktualizacje paska stanu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Widok|Włącza elementy **przybornika.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dane|Wysyła powiadomienia po zmianie pliku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dane|Włącza funkcję Zapisz jako dla typu pliku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dane|Umożliwia trwałość dla dokumentu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dane|Umożliwia pomijanie zdarzeń zmiany pliku, takich jak wyzwalanie ponownego ładowania.|
