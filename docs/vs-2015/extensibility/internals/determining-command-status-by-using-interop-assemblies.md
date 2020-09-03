---
title: Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc67123e082258932ab5df6613941f869d6049a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196787"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage musi śledzić stan poleceń, które może obsłużyć. Środowisko nie może określić, kiedy polecenie obsługiwane w pakietu VSPackage zostanie włączone lub wyłączone. Użytkownik jest odpowiedzialny za pakietu VSPackage do informowania środowiska o Stanach poleceń, na przykład o stanie poleceń ogólnych, takich jak **wycinanie**, **Kopiowanie**i **wklejanie**.  
  
## <a name="status-notification-sources"></a>Źródła powiadomień o stanie  
 Środowisko odbiera informacje o poleceniach za pomocą metody pakietów VSPackage ' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , która jest częścią implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu pakietu VSPackage. Środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę pakietu VSPackage w dwóch warunkach:  
  
- Gdy użytkownik otwiera menu główne lub menu kontekstowe (przez kliknięcie prawym przyciskiem myszy), środowisko wykonuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę we wszystkich poleceniach tego menu, aby określić ich stan.  
  
- Gdy pakietu VSPackage żąda, aby środowisko zaktualizował bieżący interfejs użytkownika (UI). Dzieje się tak, jak polecenia, które są obecnie widoczne dla użytkownika, takie jak **grupowanie,** **Kopiowanie**i **wklejanie** na standardowym pasku narzędzi, są włączone i wyłączone w odpowiedzi na akcje kontekstowe i użytkownika.  
  
  Ponieważ powłoka obsługuje wiele pakietów VSPackage, wydajność powłoki będzie nieakceptowalna, jeśli była wymagana do sondowania każdego pakietu VSPackage w celu określenia stanu polecenia. Zamiast tego pakietu VSPackage powinien aktywnie powiadamiać o środowisku, gdy jego interfejs użytkownika zmienia się w momencie zmiany. Aby uzyskać więcej informacji na temat powiadomienia o aktualizacji, zobacz [aktualizowanie interfejsu użytkownika](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Niepowodzenie powiadomienia o stanie  
 Niepowodzenie pakietu VSPackage do powiadomienia środowiska o zmianie stanu polecenia może spowodować, że interfejs użytkownika w stanie niespójnym. Należy pamiętać, że dowolne polecenia menu lub menu kontekstowego mogą być umieszczane na pasku narzędzi przez użytkownika. W związku z tym, aktualizowanie interfejsu użytkownika tylko wtedy, gdy otwierane menu lub menu kontekstowe nie jest wystarczające.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementacja](../../extensibility/internals/command-implementation.md)
