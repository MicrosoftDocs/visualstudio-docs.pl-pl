---
title: Rozwiązywanie problemów z Podglądem pomocy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8f71557dc7939e9b96c3d6cd3f2382ada69b493
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774604"
---
# <a name="troubleshooting-the-help-viewer"></a>Rozwiązywanie problemów z Podglądem Pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono problemy, które mogą wystąpić w programie Podgląd pomocy.  
  
## <a name="audio-doesnt-work"></a>Dźwięk nie działa.  
 Podgląd pomocy nie zawiera odtwarzacza audio. Jeśli pobierasz zawartość, która zawiera dźwięk i nic się nie dzieje po wybraniu **Odtwórz**, zainstaluj odtwarzacz audio.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Wyszukiwanie nie działa w systemie Windows Server 2008, Windows Server 2008 z dodatkiem SP1 lub Windows Server 2008 R2.  
 Funkcje wyszukiwania i filtrowania w Podglądzie pomocy wymagają zainstalowania usługi Windows Search i. Domyślnie ta usługa jest wyłączona w systemie Windows Server 2008, Windows Server 2008 z dodatkiem Service Pack 1 (SP1) i Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Aby aktywować usługę Windows Search  
  
1.  Uruchom Menedżera serwera.  
  
2.  W okienku nawigacji po lewej stronie wybierz **role**.  
  
3.  W okienku Podsumowanie ról wybierz **Dodaj rolę**.  
  
4.  Wybierz rolę usługi plików, a następnie wybierz **dalej** przycisku.  
  
5.  Wybierz usługę roli Windows Search.  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
 Można uzyskać więcej informacji i wyrażanie opinii na temat Podgląd pomocy za pomocą następujących zasobów:  
  
- Aby przekazać opinię, zobacz [witryny Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) na Microsoft witryny sieci Web lub Wyślij wiadomość e-mail do [ hlpfdbk@microsoft.com ](mailto:hlpfdbk@microsoft.com).  
  
- Aby uzyskać więcej informacji, zobacz [systemu pomocy i dokumentacja dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=232741) forum i [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) blogu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik administratora 2.1 podglądu pomocy](http://go.microsoft.com/fwlink/?LinkId=243985)
