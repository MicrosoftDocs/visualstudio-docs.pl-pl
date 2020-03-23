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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e53c3701e31733c54869c71820956d674ed4fb8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593697"
---
# <a name="manage-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)

Pliki zasobów to pliki, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub pliki audio. Ponieważ te pliki nie są częścią procesu kompilacji, można je zmienić bez konieczności ponownego kompilowania plików binarnych. Jeśli planujesz zlokalizować aplikację, należy użyć plików zasobów dla wszystkich ciągów i innych zasobów, które należy zmienić podczas lokalizowania aplikacji.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac).](/visualstudio/mac/managing-app-resources)

Aby uzyskać więcej informacji o zasobach w aplikacjach klasycznych platformy .NET, zobacz [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Praca z zasobami

W projekcie kodu zarządzanego otwórz okno właściwości projektu. Okno właściwości można otworzyć przez:

- Kliknięcie prawym przyciskiem myszy węzła projektu w **Eksploratorze rozwiązań** i **wybranie opcji Właściwości**
- Wpisywanie **właściwości projektu** w polu wyszukiwania **Ctrl**+**Q**
- Wybieranie **opcji Alt**+**Enter** w **Eksploratorze rozwiązań**

Wybierz kartę **Zasoby.** Można dodać plik *.resx,* jeśli projekt nie zawiera już jednego, dodać i usunąć różne rodzaje zasobów i zmodyfikować istniejące zasoby.

## <a name="resources-in-other-project-types"></a>Zasoby w innych typach projektów

Zasoby są zarządzane inaczej w projektach platformy .NET niż w innych typach projektów. Aby uzyskać więcej informacji na temat zasobów w:

- Aplikacje platformy uniwersalnej systemu Windows (UWP), zobacz [Zasoby aplikacji i system zarządzania zasobami](/windows/uwp/app-resources/)
- Projekty języka C++, zobacz [Praca z plikami zasobów](/cpp/windows/working-with-resource-files) i [Jak: Tworzenie zasobu](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Zobacz też

- [Zasoby w aplikacjach klasycznych (.NET Framework)](/dotnet/framework/resources/index)
- [Zarządzanie zasobami aplikacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-app-resources)
