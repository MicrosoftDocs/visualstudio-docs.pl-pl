---
title: 'Instrukcje: kompilowanie do wspólnego katalogu wyjściowego'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a499b5ca5ea64dd9ded10f82b1af43258f346d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284779"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Instrukcje: kompilowanie do wspólnego katalogu wyjściowego

Domyślnie program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kompiluje każdy projekt w rozwiązaniu we własnym folderze w ramach rozwiązania. Można zmienić ścieżki wyjściowe kompilacji projektów, aby wymusić umieszczenie wszystkich danych wyjściowych w tym samym folderze.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Aby umieścić wszystkie dane wyjściowe rozwiązania w wspólnym katalogu

1. Kliknij jeden projekt w rozwiązaniu.

2. W menu **projekt** kliknij polecenie **Właściwości**.

3. W zależności od typu projektu kliknij kartę **kompilacja** lub kartę **kompilacja** , a następnie ustaw **ścieżkę wyjściową** do folderu, który ma być używany dla wszystkich projektów w rozwiązaniu.

4. Powtórz kroki 1-3 dla wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Instrukcje: zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md)