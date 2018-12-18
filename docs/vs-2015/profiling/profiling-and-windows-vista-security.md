---
title: Profilowanie i Windows Vista zabezpieczeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32605cb21b79e035bba9d234cdb7b3d513417363
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772953"
---
# <a name="profiling-and-windows-vista-security"></a>Profilowanie i bezpieczeństwo systemu Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W zależności od [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] ustawień uprawnień dostępu użytkowników, które udostępnionych przez administratora komputera, użytkownik może być uprawnienia zabezpieczeń do profilowania, proces na tym komputerze. Poniższe przykłady ilustrują możliwe różnice między użytkowników:  
  
- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawił sterownik i uruchomienie usługi.  
  
- Użytkownicy domeny mogą uzyskiwać dostęp do przykładowej profilowanie tylko.  
  
- Niektórzy użytkownicy mogą uniemożliwić dostęp do profilowania, aby wszyscy inni użytkownicy.  
  
  Aby uzyskać więcej informacji, zobacz Opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Profilowanie między sesjami  
 *Profilowanie między sesjami* jest możliwość profilować proces uruchomiony w sesji logowania innego. Na przykład większość usług uruchamiane w sesji 0, a użytkownicy nie mogą uruchamiać bezpośrednio w sesji 0. Za pomocą **dołączyć do procesu** przycisk na pasku narzędzi Eksploratora wydajności lub / dołączanie opcji VSPerfCmd — narzędzie wiersza polecenia, można profilować większość procesów w sesji logowania innego.  
  
 Można wyświetlić listę procesów, które są dostępne, ustawiając opcje widoczności profilowania między procesami. Te opcje są dostępne w **dołączyć do procesu** okna, w którym jest wyświetlany po kliknięciu **dołączyć do procesu**:  
  
-   **Pokaż procesy wszystkich użytkowników**  
  
     Gdy ta opcja nie jest zaznaczona, na liście zostaną wyświetlone tylko procesy, które są własnością bieżącego użytkownika. Gdy **Pokaż procesy wszystkich użytkowników** jest zaznaczone, na liście zostaną wyświetlone procesy wszystkich użytkowników.  
  
-   **Pokaż procesy we wszystkich sesjach**  
  
     Gdy ta opcja nie jest zaznaczone, zostanie wyświetlona lista procesów w bieżącej sesji. Po wybraniu tej opcji zostanie wyświetlona lista procesy we wszystkich sesjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Porady: dołączanie do uruchomionego procesu](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)



