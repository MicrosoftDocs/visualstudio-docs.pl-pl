---
title: Zarządzanie zasobami aplikacji (.NET)
description: Dowiedz się, jak zarządzać plikami zasobów aplikacji, które nie są częścią procesu kompilacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4707a3e33279ead458566bc01ed2eed8c67355cf
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596745"
---
# <a name="manage-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)

Pliki zasobów są plikami, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub pliki audio. Ponieważ te pliki nie są częścią procesu kompilacji, można je zmienić bez konieczności ponownego kompilowania plików binarnych. Jeśli planujesz lokalizowanie aplikacji, należy używać plików zasobów dla wszystkich ciągów i innych zasobów, które należy zmienić podczas lokalizowania aplikacji.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources).

Aby uzyskać więcej informacji na temat zasobów w aplikacjach .NET, zobacz [zasoby w aplikacjach .NET](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Pracuj z zasobami

W projekcie kodu zarządzanego Otwórz okno właściwości projektu. Aby otworzyć okno właściwości, można wykonać jedną z:

- Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**
- Wpisywanie **właściwości projektu** w **Ctrl** + polu wyszukiwania Ctrl **Q**
- Wybieranie **klawisza** + **Enter** w **Eksplorator rozwiązań**

Wybierz kartę **zasoby** . Plik *. resx* można dodać, jeśli projekt nie zawiera już jednego z nich, dodawać i usuwać różne rodzaje zasobów oraz modyfikować istniejące zasoby.

## <a name="resources-in-other-project-types"></a>Zasoby w innych typach projektów

Zasoby są zarządzane inaczej w projektach .NET niż w innych typach projektów. Aby uzyskać więcej informacji na temat zasobów w programie:

- Aplikacje platforma uniwersalna systemu Windows (platformy UWP), zobacz [zasoby aplikacji i system zarządzania zasobami](/windows/uwp/app-resources/)
- Projekty języka C++, zobacz [Work with pliki zasobów](/cpp/windows/working-with-resource-files) i [instrukcje: Tworzenie zasobu](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Zobacz także

- [Zasoby w aplikacjach .NET (.NET Framework)](/dotnet/framework/resources/index)
- [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources)
