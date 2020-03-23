---
title: Tworzenie i edytowanie konfiguracji kompilacji
description: W tym artykule opisano tworzenie konfiguracji kompilacji w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 09591cb4feee4e9dc673f925bf3917eb3d07319b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983583"
---
# <a name="creating-and-editing-build-configurations"></a>Tworzenie i edytowanie konfiguracji kompilacji

Konfiguracje kompilacji mogą być tworzone dla poszczególnych projektów lub na podstawie całego rozwiązania. Te konfiguracje zapewniają precyzyjną kontrolę nad kompilacją.

Menu opcji zarówno dla projektów, jak i rozwiązań zapewnia obszar do tworzenia i edytowania nowych i istniejących konfiguracji.

## <a name="creating-a-project-build-configurations"></a>Tworzenie konfiguracji kompilacji projektu

Aby utworzyć konfigurację kompilacji projektu, należy wykonać następujące kroki:

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Opcje**.

2. W oknie dialogowym Opcje projektu wybierz pozycję **Buduj > Konfiguracje:**

    ![Menedżer konfiguracji w opcjach projektu](media/create-and-edit-configurations-image2.png)

3. Aby utworzyć nową konfigurację, wybierz pozycję **Dodaj**. Alternatywnie można skopiować jedną z istniejących konfiguracji.

Po utworzeniu konfiguracji można użyć sekcji **Kompilacja** w opcjach projektu, aby dostosować właściwości odpowiednie do konfiguracji:

![Konfigurowanie opcji kompilacji](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Tworzenie konfiguracji kompilacji rozwiązania

Aby utworzyć konfigurację kompilacji rozwiązania, należy wykonać następujące kroki:

1. Kliknij prawym przyciskiem myszy węzeł Rozwiązanie i wybierz polecenie **Opcje**.

2. W oknie dialogowym Opcje rozwiązania wybierz pozycję **Kompilacja > konfiguracje:**

    ![Menedżer konfiguracji w opcjach rozwiązania](media/create-and-edit-configurations-image1.png)

3. Aby utworzyć nową konfigurację, wybierz pozycję **Dodaj**. Alternatywnie można skopiować jedną z istniejących konfiguracji.

Po utworzeniu konfiguracji można użyć sekcji **Kompilacja** w opcjach każdego projektu, aby dostosować właściwości odpowiednie do konfiguracji:

![Konfigurowanie opcji kompilacji](media/create-and-edit-configurations-image3.png)

## <a name="editing-a-build-configuration"></a>Edytowanie konfiguracji kompilacji

Aby zmienić nazwę konfiguracji, wybierz ją z listy Konfiguracja w opcji projektu lub rozwiązania:

![lista konfiguracji](media/create-and-edit-configurations-image4.png)

Wybierz przycisk **Zmień nazwę.**

![zmienianie nazwy okna dialogowego](media/create-and-edit-configurations-image5.png)

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Zobacz też

- [Tworzenie i edytowanie konfiguracji kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)