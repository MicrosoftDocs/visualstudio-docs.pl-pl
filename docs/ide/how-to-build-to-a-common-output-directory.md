---
title: 'Instrukcje: kompilowanie do wspólnego katalogu wyjściowego'
description: Dowiedz się, jak można zmienić ścieżki wyjściowe kompilacji dla projektów, aby wymusić umieszczenie wszystkich danych wyjściowych w tym samym folderze.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e2abb9a768621477465b753554c111126a5af98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967621"
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