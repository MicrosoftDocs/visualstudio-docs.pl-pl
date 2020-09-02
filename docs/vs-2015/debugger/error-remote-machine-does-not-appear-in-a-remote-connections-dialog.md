---
title: 'Błąd: maszyna zdalna nie jest wyświetlana w oknie dialogowym połączeń zdalnych | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697329"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Błąd: Komputer zdalny nie jest wyświetlany w oknie dialogowym połączeń zdalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli maszyna zdalna nie jest wyświetlana w oknie dialogowym połączenia zdalne, należy sprawdzić następujące typowe przyczyny.  
  
 Jeśli używasz zarządzanego trybu zgodności, zapoznaj się z dokumentacją programu Visual Studio 2010: [Rozwiązywanie problemów z debugowaniem zdalnym — Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Typowe przyczyny tego błędu  
  
- Maszyna zdalna jest uruchomiona na komputerze znajdującym się w innej podsieci. Aby rozwiązać ten problem, ręcznie wpisz nazwę lub adres IP komputera w oknie dialogowym kwalifikator  
  
- Zdalny debuger nie jest uruchomiony na komputerze zdalnym. Aby rozwiązać ten problem, uruchom zdalny debuger.  
  
- Zapora blokuje komunikację między programem Visual Studio i komputerem zdalnym. Aby rozwiązać ten problem, należy skonfigurować zaporę tak, aby zezwalała na komunikację programu Visual Studio i zdalnego debugera (msvsmon).  
  
- Oprogramowanie antywirusowe blokuje komunikację między programem Visual Studio i komputerem zdalnym. Aby rozwiązać ten problem, Skonfiguruj oprogramowanie antywirusowe, aby umożliwić komunikację programu Visual Studio i zdalnego debugera (msvsmon).  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
