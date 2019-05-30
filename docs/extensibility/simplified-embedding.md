---
title: Uproszczone osadzanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c77c7f19ff677ddbe8339c88ef3ea46953e23b7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332074"
---
# <a name="simplified-embedding"></a>Uproszczone osadzanie
Uproszczone osadzanie jest włączona w edytorze, po jego obiekt widoku dokumentu jest elementem nadrzędnym (czyli przeprowadzone elementu podrzędnego) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejs jest implementowany jej okna poleceń. Uproszczone osadzanie edytory nie może obsługiwać aktywny formant. Obiekty, używany do tworzenia edytora za pomocą uproszczone osadzanie przedstawiono na poniższej ilustracji.

 ![Uproszczone osadzanie w edytorze grafiki](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") edytor z uproszczone osadzanie

> [!NOTE]
> Obiektów na tej ilustracji tylko `CYourEditorFactory` obiektu jest wymagana do utworzenia standardowy edytor opartych na plikach. Jeśli tworzysz niestandardowy edytor, nie należy implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, ponieważ edytor prawdopodobnie będzie mieć własny mechanizm prywatnej trwałości. Dla innych niestandardowych edytorów jednak należy to zrobić.

 Wszystkie interfejsy zaimplementowane do tworzenia edytora za pomocą uproszczone osadzanie są zawarte w `CYourEditorDocument` obiektu. Jednak do obsługi wielu widoków danych dokumentu, Podziel interfejsy na osobne dane i przeglądać obiekty zgodnie z instrukcjami w poniższej tabeli.

|Interface|Lokalizacja interfejsu|Zastosowanie|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Widok|Udostępnia połączenie do okna nadrzędnego.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Widok|Obsługuje polecenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Widok|Włącza aktualizacje paska stanu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Widok|Włącza **przybornika** elementów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dane|Wysyła powiadomienia po zmianie pliku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dane|Włącza funkcję Zapisz jako dla typu pliku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dane|Umożliwia utrwalanie w dokumencie.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dane|Umożliwia pomijanie zdarzeń zmiany plików, takie jak wyzwolenie Załaduj ponownie.|