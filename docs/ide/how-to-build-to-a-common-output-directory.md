---
title: 'Instrukcje: Kompilowanie do wspólnego katalogu wyjściowego'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea36368a60fc08d6a818d1ca1e66cfb92d814478
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030772"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Instrukcje: Kompilowanie do wspólnego katalogu wyjściowego

Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kompilacje poszczególnych projektów w rozwiązaniu w jego własnym folderze wewnątrz rozwiązania. Można zmienić ścieżki danych wyjściowych kompilacji projektów, aby wymusić wszystkie dane wyjściowe mają być umieszczone w tym samym folderze.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Aby umieścić wszystkie rozwiązania w dane wyjściowe wspólnego katalogu

1.  Polecenie jednego projektu w rozwiązaniu.

2.  Na **projektu** menu, kliknij przycisk **właściwości**.

3.  W zależności od typu projektu, kliknij w dowolnym **skompilować** karty lub **kompilacji** , a następnie ustaw **ścieżkę wyjściową** do folderu, do użycia dla wszystkich projektów w rozwiązaniu.

4.  Powtórz kroki 1 – 3 dla wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Instrukcje: Zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md)