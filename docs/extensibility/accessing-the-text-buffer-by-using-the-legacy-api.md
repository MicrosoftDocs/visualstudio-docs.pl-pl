---
title: Dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661bf39e82fef5c040861bc9386dcb7f897d25cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313630"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API
Tekst jest odpowiedzialny za zarządzanie strumienie tekstu i trwałość plików zapewnianą. Mimo że bufor może odczytać lub zapisać innych formatów, cała komunikacja zwykłych z buforu odbywa się przy użyciu standardu Unicode. W starszych interfejsów API bufor tekstowy można użyć do identyfikowania lokalizacji znak w buforze jedno - lub dwuwymiarowy współrzędnych.

## <a name="one--and-two-dimension-coordinate-systems"></a>Wymiar jednego i dwóch koordynacji systemów
 Jednowymiarowy pozycji współrzędnych opiera się na pozycji znaku od pierwszego znaku w buforze, takich jak 147. Możesz użyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfejsu, aby uzyskać dostęp do jednowymiarowego lokalizacji w buforze. Dwuwymiarowa współrzędnych opiera się na pary wiersza oraz indeksu. Na przykład znak w buforze, od 43 5 będzie w wierszu 43, pięć znaków z prawej strony pierwszego znaku w danym wierszu. Dostęp dwuwymiarową lokalizację w buforze, używając <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfejsu. Zarówno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfejsów implementowanych przez obiekt buforu tekstu (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) i jest dostępny od siebie przy użyciu `QueryInterface`. Na poniższym diagramie przedstawiono te i inne kluczowe interfejsy na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

 ![Obiekt buforu tekstu](../extensibility/media/vstextbuffer.gif "vsTextBuffer") obiekt buforu tekstu

 Mimo że albo współrzędnych działa w buforze tekstu, zoptymalizowane pod kątem używania dwuwymiarowe współrzędne. Jednowymiarowy współrzędnych można utworzyć zmniejszenie wydajności. Dlatego należy używać dwuwymiarową współrzędnych zawsze, gdy jest to możliwe.

 Tekst odpowiedzialność za drugim bufor jest trwałość plików zapewnianą. Aby to zrobić, implementuje obiekt buforu tekstu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> i działa jako składnik obiekcie danych dokumentów dla elementów projektu i inne składniki środowiska zaangażowanych w trwałości. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md).

## <a name="in-this-section"></a>W tej sekcji
- [Zmień ustawienia widoku przy użyciu starszej wersji interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md) wyjaśnia, jak zmienić ustawienia widoku przy użyciu starszej wersji interfejsu API.

- [Ustawienia globalne monitorowanie za pomocą Menedżera tekstu](../extensibility/using-the-text-manager-to-monitor-global-settings.md) wyjaśnia, jak monitorować ustawienia globalne przy użyciu Menedżera tekstu.

## <a name="see-also"></a>Zobacz także
- [W edytorze podstawowych](../extensibility/inside-the-core-editor.md)