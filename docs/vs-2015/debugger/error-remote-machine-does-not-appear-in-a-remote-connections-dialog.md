---
title: 'Błąd: Komputer zdalny nie jest wyświetlana w oknie dialogowym połączeń zdalnych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a97211c1fa86123a2a7a65f2ff86b0cecac957dc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697329"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Błąd: Maszyna zdalna nie jest wyświetlana w oknie dialogowym połączeń zdalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli komputer zdalny nie zostanie wyświetlony w oknie dialogowym połączeń zdalnych, sprawdź następujące typowe przyczyny.  
  
 Jeśli używasz trybu zgodności zarządzanej, sprawdź w dokumentacji programu Visual Studio 2010: [Rozwiązywanie problemów z debugowaniem zdalnym — program Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Typowe przyczyny tego błędu  
  
- Komputer zdalny jest uruchomiona na komputerze, na którym znajduje się w innej podsieci. Aby rozwiązać ten problem, ręcznie wpisać nazwę lub adres IP w oknie dialogowym kwalifikatora  
  
- Zdalny debuger nie jest uruchomiona na komputerze zdalnym. Aby rozwiązać ten problem, uruchom zdalny debuger.  
  
- Zapora blokuje komunikację między Visual Studio i komputera zdalnego. Aby rozwiązać ten problem, Skonfiguruj zaporę, aby umożliwić komunikowania się programu Visual Studio i zdalny debuger (msvsmon).  
  
- Oprogramowanie antywirusowe blokuje komunikację między Visual Studio i komputera zdalnego. Aby rozwiązać ten problem, należy skonfigurować oprogramowanie antywirusowe, aby zezwolić na program Visual Studio i zdalny debuger (msvsmon), do komunikowania się.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
