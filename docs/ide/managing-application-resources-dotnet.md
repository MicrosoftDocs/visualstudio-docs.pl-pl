---
title: Zarządzanie zasobami aplikacji (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9a80a84276648f8a0f0d5a94992b5f58cbcfefa
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348138"
---
# <a name="manage-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)

Pliki zasobów są pliki, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub pliki audio. Ponieważ te pliki nie są częścią procesu kompilacji, można je zmienić, bez konieczności ponownego kompilowania plików binarnych. Jeśli planowane jest zlokalizować aplikację, należy użyć plików zasobów dla wszystkich ciągów i innych zasobów, które muszą zostać zmienione podczas lokalizowania aplikacji.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources).

Aby uzyskać więcej informacji na temat zasobów w aplikacjach klasycznych .NET, zobacz [zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Praca z zasobami

W projekcie kodu zarządzanego Otwórz okno właściwości projektu. W oknie właściwości można otworzyć przez:

- Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając polecenie **właściwości**
- Wpisz "właściwości projektu" w **Szybkie uruchamianie** okna
- Wybieranie **Alt**+**wprowadź** w **Eksploratora rozwiązań**

Wybierz **zasobów** kartę. Możesz dodać *resx* plik, jeśli projekt nie zawiera jeden już, dodawanie i usuwanie różnych rodzajów zasobów i zmodyfikowania istniejących zasobów.

## <a name="resources-in-other-project-types"></a>Zasoby w innych typów projektów

Zasoby są zarządzane w różny sposób w projektach platformy .NET niż w innych typów projektów. Aby uzyskać więcej informacji na temat zasobów:

- Aplikacje uniwersalne platformy Windows (UWP), zobacz [zasobów aplikacji i systemu zarządzania zasobów](/windows/uwp/app-resources/)
- Projekty języka C++, zobacz [pracy z plikami zasobów](/cpp/windows/working-with-resource-files) i [porady: tworzenie zasobu](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Zobacz także

- [Zasoby w aplikacjach komputerowych (.NET Framework)](/dotnet/framework/resources/index)
- [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources)
