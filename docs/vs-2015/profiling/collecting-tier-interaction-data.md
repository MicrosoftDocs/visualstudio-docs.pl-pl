---
title: Zbieranie danych o interakcji między warstwami | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: a20266c870316be9b6be67e661d13eb4e6fdbaee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568050"
---
# <a name="collecting-tier-interaction-data"></a>Zbieranie danych o interakcji między warstwami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje na temat czasu wykonania funkcji aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem usług ADO.NET. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej.  
  
 **Visual Studio editions**  
  
 Dane profilowania interakcji między warstwami można zbierać w programach Visual Studio Ultimate, Visual Studio Premium lub Visual Studio Professional. Natomiast obejrzeć takie dane można wyświetlić tylko w programie VS Ultimate i Premium programu VS.  
  
 **System Windows 8 i Windows Server 2012**  
  
 Aby zebrać dane interakcji między warstwami na aplikacje pulpitu systemu Windows 8 i aplikacje systemu Windows Server 2012, należy użyć metody instrumentacji. Nie można zebrać dane interakcji między warstwami aplikacji Windows Store. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Dane interakcji między warstwami można uwzględnić w wszystkich metod profilowania w innych obsługiwanych wersji systemu Windows.  
  
 **Kreator wydajności**  
  
 Ze względu na błąd Kreatora wydajności należy dodać opcji zbierania danych interakcji warstwy do uruchomienia profilowania z poziomu Eksploratora wydajności. Do węzła docelowego Eksploratora wydajności, należy dodać projekt, plik wykonywalny lub witryny sieci Web.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Aby dodać dane interakcji między warstwami do profilowania za pomocą stron właściwości sesji wydajności  
  
1. W Eksploratorze wydajności, wybierz **właściwości** z menu kontekstowego.  
  
2. Wybierz **interakcje warstw** strony, a następnie sprawdź **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru.  
  
3. W Eksploratorze wydajności wybierz **cele** węzła, a następnie określ project, plik wykonywalny lub witryny sieci web, które powinny być profilowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok interakcji między warstwami](../profiling/tier-interactions-view.md)
