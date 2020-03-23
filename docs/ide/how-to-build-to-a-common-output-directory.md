---
title: 'Jak: Tworzenie do wspólnego katalogu wyjściowego'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
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
ms.openlocfilehash: a1e669789d2117b4bd2ee550dfffb147e46620c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68416744"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Jak: Tworzenie do wspólnego katalogu wyjściowego

Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tworzy każdy projekt w rozwiązaniu w swoim własnym folderze wewnątrz rozwiązania. Można zmienić ścieżki wyjściowe kompilacji projektów, aby wymusić wszystkie dane wyjściowe, które mają być umieszczone w tym samym folderze.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Aby umieścić wszystkie wyjścia rozwiązania we wspólnym katalogu

1. Kliknij jeden projekt w rozwiązaniu.

2. W menu **Projekt** kliknij polecenie **Właściwości**.

3. W zależności od typu projektu kliknij kartę **Skompiluj** lub na karcie **Kompilacja** i ustaw **ścieżkę danych wyjściowych** do folderu, który będzie używany dla wszystkich projektów w rozwiązaniu.

4. Powtórz kroki 1-3 dla wszystkich projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Jak: Zmiana katalogu wyjściowego kompilacji](../ide/how-to-change-the-build-output-directory.md)