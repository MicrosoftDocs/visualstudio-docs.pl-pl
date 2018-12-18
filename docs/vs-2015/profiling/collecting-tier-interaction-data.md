---
title: Zbieranie danych o interakcji między warstwami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e2d46992b48b987966bac7d7dc68787f4016c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761189"
---
# <a name="collecting-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje na temat czasu wykonania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej.  
  
 **Wersje programu Visual Studio**  
  
 Dane profilowania interakcji między warstwami można zbierać w programach Visual Studio Ultimate, Visual Studio Premium lub Visual Studio Professional. Natomiast obejrzeć takie dane można wyświetlić tylko w programie VS Ultimate i Premium programu VS.  
  
 **System Windows 8 i Windows Server 2012**  
  
 Aby zebrać dane interakcji między warstwami na aplikacje pulpitu systemu Windows 8 i aplikacje systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zebrać dane interakcji między warstwami aplikacji Windows Store. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Dane interakcji między warstwami można uwzględnić w wszystkich metod profilowania w innych obsługiwanych wersji systemu Windows.  
  
 **Kreator wydajności**  
  
 Ze względu na błąd Kreatora wydajności należy dodać opcji zbierania danych interakcji warstwy do uruchomienia profilowania z poziomu Eksploratora wydajności. Do węzła docelowego Eksploratora wydajności, należy dodać projekt, plik wykonywalny lub witryny sieci Web.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać dane interakcji między warstwami do profilowania za pomocą stron właściwości sesji wydajności  
  
1.  W Eksploratorze wydajności, wybierz **właściwości** z menu kontekstowego.  
  
2.  Wybierz **interakcje warstw** strony, a następnie sprawdź **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.  
  
3.  W Eksploratorze wydajności wybierz **cele** węzła, a następnie określ project, plik wykonywalny lub witryny sieci web, które powinny być profilowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok interakcji między warstwami](../profiling/tier-interactions-view.md)



