---
title: 'DA0003: Wiele przykładów jądra | Dokumentacja firmy Microsoft'
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
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 922cc6998db9813c188eb9028b8e855a8b860270
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741692"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Wiele przykładów jądra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0003 |  
| Kategoria | Profilowanie użycia narzędzia |  
| Profilowanie metody | Próbkowanie |  
| Komunikat | Masz dużą część próbek w trybie jądra. To może wskazywać dużą aktywność We/Wy lub wysokie tempo przełączania kontekstu. Należy wziąć pod uwagę aplikacji z użyciem trybu instrumentacji. |  
| Typ reguły | Informacji |  
  
## <a name="cause"></a>Przyczyna  
 Znaczna część przykłady stosu wywołań, które zostały zebrane dla aplikacji zostały wykonywania w trybie jądra. Należy wziąć pod uwagę, profilowanie aplikacji przy użyciu innej metody profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 W Windows kod może być wykonywana w trybie jądra lub w trybie użytkownika. (Tryb jądra jest również nazywane trybie uprzywilejowanym). Tylko kod niskiego poziomu systemu, takie jak sterowniki urządzeń, działa w trybie jądra. Aplikacja w trybie użytkownika, można przejść do trybu jądra do wykonywania operacji We/Wy, poczekaj, aż wątek lub procesu synchronizacji w nim elementów podstawowych lub wykonać wywołania systemowe.  
  
 Próbkowanie jest najbardziej efektywne w przypadku profilowania aplikacji, które spędzają większość czasu wykonywania pracy w trybie użytkownika. Liczba próbek, które zostały zebrane podczas wykonywania aplikacji w trybie jądra można wskazać częstych operacji We/Wy lub może wskazywać tego kontekstu, w których występują przełączników. Żadna z tych operacji można sprawdzić przy użyciu metody próbkowania. Podjęto zbyt wiele przykładów trybu jądra, dane z próbkowania może nie zawierać wystarczającej liczby próbek trybu użytkownika będzie statystycznie istotne.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Należy wziąć pod uwagę profilowania aplikację ponownie przy użyciu jednego z następujących opcji:  
  
-   Profile, przy użyciu metody instrumentacji.  
  
-   Zwiększ częstotliwość próbkowania w celu próbuje zebrać więcej przykładów w trybie użytkownika.



