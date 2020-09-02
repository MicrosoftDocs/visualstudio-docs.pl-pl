---
title: Profilowanie i zabezpieczenia systemu Windows Vista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7e485bc6289634e1bb6d4b4106d54c8dc82096b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683703"
---
# <a name="profiling-and-windows-vista-security"></a>Profilowanie i bezpieczeństwo systemu Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W zależności od [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] ustawień uprawnień dostępu użytkownika dostępnych dla administratora komputera każdy użytkownik może mieć uprawnienia zabezpieczeń do profilowania procesu na tym komputerze. Poniższe przykłady ilustrują ewentualne różnice między użytkownikami:  
  
- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.  
  
- Użytkownicy domeny mogą uzyskać dostęp tylko do profilowania przykładowych.  
  
- Niektórzy użytkownicy mogą odmówić dostępu do profilowania wszystkim innym użytkownikom.  
  
  Aby uzyskać więcej informacji, zobacz Opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Profilowanie między sesjami  
 *Profilowanie między sesjami* to możliwość profilowania procesu, który jest uruchamiany w innej sesji logowania. Na przykład większość usług jest uruchomionych w sesji 0, a użytkownicy nie mogą być uruchamiani bezpośrednio w sesji 0. Za pomocą przycisku **Dołącz do procesu** na pasku narzędzi Eksplorator wydajności lub opcji/Attach narzędzia wiersza polecenia VSPerfCmd można profilować większość procesów w różnych sesjach logowania.  
  
 Listę procesów, które są dostępne, można wyświetlić, ustawiając opcje widoczności profilowania między procesami. Te opcje są dostępne w oknie **Dołącz do procesu** , który jest wyświetlany po kliknięciu przycisku **Dołącz do procesu**:  
  
- **Pokaż procesy wszystkich użytkowników**  
  
     Gdy ta opcja nie jest zaznaczona, na liście zostaną wyświetlone tylko te procesy, których właścicielem jest bieżący użytkownik. W przypadku wybrania opcję **Pokaż procesy wszystkich użytkowników** na liście wyświetlane są procesy wszystkich użytkowników.  
  
- **Pokaż procesy we wszystkich sesjach**  
  
     Gdy ta opcja nie jest zaznaczona, na liście są wyświetlane procesy w bieżącej sesji. Gdy ta opcja jest zaznaczona, na liście są wyświetlane procesy we wszystkich sesjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Instrukcje: dołączanie do uruchomionego procesu](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)
