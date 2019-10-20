---
title: Zarządzanie zasobami aplikacji (.NET)
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29e4fbbd8d50001807f3d90a82d18e40a3674d01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654252"
---
# <a name="manage-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)

Pliki zasobów są plikami, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub pliki audio. Ponieważ te pliki nie są częścią procesu kompilacji, można je zmienić bez konieczności ponownego kompilowania plików binarnych. Jeśli planujesz lokalizowanie aplikacji, należy używać plików zasobów dla wszystkich ciągów i innych zasobów, które należy zmienić podczas lokalizowania aplikacji.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources).

Aby uzyskać więcej informacji o zasobach w aplikacjach klasycznych platformy .NET, zobacz [zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Pracuj z zasobami

W projekcie kodu zarządzanego Otwórz okno właściwości projektu. Aby otworzyć okno właściwości, można wykonać jedną z:

- Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**
- Wpisywanie **właściwości projektu** w polu wyszukiwania **Ctrl** +**Q**
- Wybieranie **Alt** +**Enter** in **Eksplorator rozwiązań**

Wybierz kartę **zasoby** . Plik *. resx* można dodać, jeśli projekt nie zawiera już jednego z nich, dodawać i usuwać różne rodzaje zasobów oraz modyfikować istniejące zasoby.

## <a name="resources-in-other-project-types"></a>Zasoby w innych typach projektów

Zasoby są zarządzane inaczej w projektach .NET niż w innych typach projektów. Aby uzyskać więcej informacji na temat zasobów w programie:

- Aplikacje platforma uniwersalna systemu Windows (platformy UWP), zobacz [zasoby aplikacji i system zarządzania zasobami](/windows/uwp/app-resources/)
- C++projekty, zobacz [pracy z plikami zasobów](/cpp/windows/working-with-resource-files) i [instrukcje: Tworzenie zasobu](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Zobacz także

- [Zasoby w aplikacjach klasycznych (.NET Framework)](/dotnet/framework/resources/index)
- [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources)
