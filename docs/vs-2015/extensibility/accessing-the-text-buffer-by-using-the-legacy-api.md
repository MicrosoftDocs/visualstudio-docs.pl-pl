---
title: Uzyskiwanie dostępu do buforu tekstowego przy użyciu starszej wersji interfejsu API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185009"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Uzyskiwanie dostępu do buforu tekstowego przy użyciu starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tekst jest odpowiedzialny za zarządzanie strumieniami tekstu i trwałością plików. Mimo że bufor może odczytywać lub zapisywać inne formaty, cała zwykła komunikacja z buforem jest wykonywana za pomocą Unicode. W starszych interfejsach API bufor tekstu może używać jednego lub dwuwymiarowego układu współrzędnych do identyfikowania lokalizacji znaków w buforze.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Systemy współrzędnych jeden-i dwa-wymiarowe  
 Pozycja współrzędnej jednowymiarowej jest oparta na pozycji znaku z pierwszego znaku w buforze, na przykład 147. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>Interfejs umożliwia dostęp do jednowymiarowej lokalizacji w buforze. Dwuwymiarowy układ współrzędnych jest oparty na parach wierszy i indeksów. Na przykład znak w buforze w 43, 5 powinien znajdować się w wierszu 43, pięć znaków z prawej strony pierwszego znaku w tym wierszu. Użytkownik uzyskuje dostęp do dwuwymiarowej lokalizacji w buforze przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfejsu. Oba <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfejsy i są implementowane przez obiekt buforu tekstu ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ) i mogą być od siebie dostępne za pomocą `QueryInterface` . Na poniższym diagramie przedstawiono te i inne kluczowe interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Obiekt buforu tekstu](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Obiekt buforu tekstu  
  
 Chociaż system współrzędnych działa w buforze tekstu, jest zoptymalizowany pod kątem używania współrzędnych dwuwymiarowych. Jednowymiarowy układ współrzędnych może spowodować narzut wydajności. W związku z tym należy używać dwuwymiarowego układu współrzędnych, gdy jest to możliwe.  
  
 Drugą odpowiedzialnością bufora tekstu jest trwałość pliku. W tym celu obiekt buforu tekstu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> i działa jako składnik obiektu danych dokumentu dla elementów projektu i innych składników środowiska związanych z trwałością. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zmienianie ustawień widoku za pomocą starszego interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Wyjaśnia, jak zmienić ustawienia widoku przy użyciu starszego interfejsu API.  
  
 [Używanie menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Wyjaśnia, jak za pomocą Menedżera tekstów monitorować ustawienia globalne...  
  
## <a name="see-also"></a>Zobacz też  
 [Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)
