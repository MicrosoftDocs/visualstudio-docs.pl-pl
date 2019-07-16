---
title: Visual Studio Shell | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ec79aab58e167ff2c935317897ba10a042a2e5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180367"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Shell jest podstawowym agenta integracji w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Powłoki zapewnia niezbędne funkcje umożliwiające pakietów VSPackage udostępnić wspólne usługi. Ponieważ architektury celem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] się w pakietach VSPackage, uprawnienia nabywa podstawowe funkcje powłoki jest to platforma do zapewnienia podstawowej funkcjonalności i obsługi cross komunikacji między jej składowe pakietów VSPackage.  
  
## <a name="shell-responsibilities"></a>Obowiązki powłoki  
 Powłoka ma następujące obowiązki klucza:  
  
- Obsługa (za pośrednictwem interfejsów COM) podstawowych elementów interfejsu użytkownika (UI). Należą do domyślnych menu i paski narzędzi, ramki okna dokumentu lub okna podrzędne interfejsu wielu dokumentów (MDI) i ramki okna narzędzia i obsługę dokującej.  
  
- Utrzymanie uruchomionej listę wszystkich aktualnie otwarte dokumenty w uruchomionej tabeli dokumentu (Normalizacją) w celu skoordynowania trwałości dokumentów i w celu zagwarantowania, że nie można otworzyć tego jednego dokumentu, w więcej niż jeden sposób lub w sposób niezgodny.  
  
- Obsługa interfejsu routing poleceń i polecenia obsługi `IOleCommandTarget`.  
  
- Ładowanie pakietów VSPackage w odpowiednim czasie. Opóźnienie podczas ładowania pakietu VSPackage jest poprawa wydajności powłoki.  
  
- Zarządzanie niektórych udostępnionych usług, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, która zapewnia funkcje podstawowe powłoki i <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, która dostarcza funkcje podstawowe obsługi okien.  
  
- Zarządzanie plikami rozwiązania (.sln). Rozwiązania zawierać grup powiązanych projektów, podobne do obszaru roboczego (.dsw) plików w Visual C++ 6.0.  
  
- Zaznaczenie całego powłoki śledzenia, kontekstu i waluty. Powłoka śledzi następujące elementy:  
  
  - Bieżący projekt  
  
  - Bieżący element projektu lub bieżący identyfikator elementu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
  - Bieżące zaznaczenie dla **właściwości** okna lub `SelectionContainer`  
  
  - Kontekstu interfejsu użytkownika lub identyfikatory CmdUIGuids, który kontrolowanie widoczności elementu polecenia, menu i paski narzędzi  
  
  - Aktualnie aktywnych elementów, takich jak aktywne okno dokumentu i menedżera cofania  
  
  - Atrybuty kontekstu użytkownika, które dysku dynamiczna pomoc  
  
  Powłoka pośredniczy również komunikację między bieżącym usług i zainstalowanych pakietów VSPackage. Obsługuje podstawowe funkcje powłoki i udostępnienie ich dla wszystkich pakietów VSPackage zintegrowane w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Te podstawowe funkcje obejmują następujące elementy:  
  
- **Temat** ekranu okna dialogowego pole i ekranu powitalnego  
  
- **Dodaj nowy i Dodaj istniejący element** okien dialogowych  
  
- **Widok klas** okna i **przeglądarki obiektów**  
  
- **Odwołania** okno dialogowe  
  
- **Konspekt dokumentu** okna  
  
- **Dynamiczna Pomoc** okna  
  
- **Znajdź** i **zastąpienia**  
  
- **Otwórz projekt** i **Otwórz plik** okien dialogowych na **New** menu  
  
- **Opcje** okno dialogowe na **narzędzia** menu  
  
- **Właściwości** okna  
  
- **Eksplorator rozwiązań**  
  
- **Lista zadań** okna  
  
- **Przybornik**  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
