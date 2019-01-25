---
title: Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798189"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage musi zachować informacje o stanie poleceń, które może obsłużyć. Środowisko nie może określić, kiedy polecenie przetwarzanych w ramach Twojego pakietu VSPackage staje się włączone lub wyłączone. Jest odpowiedzialny za Twojego pakietu VSPackage poinformować środowiska o stanach polecenia, na przykład stanu Generalny polecenia, takie jak **Wytnij**, **kopiowania**, i **Wklej**.  
  
## <a name="status-notification-sources"></a>Stan powiadomienia źródeł  
 Środowisko otrzymuje informacji na temat poleceń w pakietach VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody, która jest częścią pakietu VSPackage implementacji programu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Wywołania środowiska <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda pakietu VSPackage w dwóch okolicznościach:  
  
- Gdy użytkownik otwiera menu głównego lub menu kontekstowego (na przykład przez kliknięcie prawym przyciskiem myszy), wykonuje środowiska <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody na wszystkich poleceń tym menu, aby określić ich stanu.  
  
- Gdy pakietu VSPackage żąda, że środowisko aktualizacji bieżący interfejsu użytkownika (UI). Dzieje się tak jak polecenia, które są obecnie widoczne dla użytkownika, takie jak **Wytnij**, **kopiowania**, i **Wklej** grupowania na standardowym pasku narzędzi, stają się włączone i wyłączone w odpowiedzi na działania kontekstu i użytkownika.  
  
  Ponieważ powłoki hostuje wiele pakietów VSPackage, wydajności powłoki programu nieakceptowalnie może obniżyć razie zostały sondować każdego pakietu VSPackage, aby określić stan polecenia. Zamiast tego Twojego pakietu VSPackage powinny aktywnie powiadomić środowiska, zmianie jego interfejsu użytkownika w momencie zmiany. Aby uzyskać więcej informacji na temat powiadomienie o aktualizacji, zobacz [aktualizowania interfejsu użytkownika](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Stan: niepowodzenie powiadomień  
 Błąd usługi pakietu VSPackage powiadomić środowiska zmiany stanu polecenia można umieścić interfejsu użytkownika w stanie niespójnym. Należy pamiętać, że dowolne polecenia menu menu lub kontekst można umieścić na pasku narzędzi przez użytkownika. W związku z tym aktualizowania interfejsu użytkownika, tylko wtedy, gdy zostanie otwarte menu menu lub kontekst nie jest wystarczająca.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementacja](../../extensibility/internals/command-implementation.md)
