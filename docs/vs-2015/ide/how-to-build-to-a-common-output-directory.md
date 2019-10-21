---
title: 'Instrukcje: kompilowanie do wspólnego katalogu wyjściowego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f85ff51b93383d2deca409a00a3db130d52b5003
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645415"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Porady: budowanie wspólnego katalogu wyjściowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kompiluje każdy projekt w rozwiązaniu we własnym folderze w ramach rozwiązania. Można zmienić ścieżki wyjściowe kompilacji projektów, aby wymusić umieszczenie wszystkich danych wyjściowych w tym samym folderze.

### <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Aby umieścić wszystkie dane wyjściowe rozwiązania w wspólnym katalogu

1. Kliknij jeden projekt w rozwiązaniu.

2. W menu **projekt** kliknij polecenie **Właściwości**.

3. W zależności od typu projektu kliknij kartę **kompilacja** lub kartę **kompilacja** , a następnie ustaw **ścieżkę wyjściową** do folderu, który ma być używany dla wszystkich projektów w rozwiązaniu.

4. Powtórz kroki 1-3 dla wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz też
 [Kompilowanie i kompilowanie](../ide/compiling-and-building-in-visual-studio.md) [metody: zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md)
