---
title: Szablon projektu VSIX | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697933"
---
# <a name="vsix-project-template"></a>Szablon projektu VSIX

Za pomocą szablonu projektu VSIX można zawinąć co najmniej jedno rozszerzenie programu Visual Studio w projekcie VSIX, a następnie opublikować pakiet w witrynie sieci Web [programu Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

 Wdrożenie VSIX obsługuje vspackages, zestawy, składniki MEF, szablony projektów, szablony elementów, formanty przybornika i niestandardowe typy rozszerzeń.

> [!NOTE]
> Aby używać projektów VSIX, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji na temat sdk programu Visual Studio, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Gdzie znaleźć szablon projektu VSIX

Szablon projektu VSIX jest dostępny w oknie dialogowym **Nowy projekt,** wyszukując "vsix".  Istnieje zarówno c# i Visual Basic wersji.

> [!TIP]
> Należy upewnić się, że program .NET Framework 4.5 lub nowszy jest określony w polu listy rozwijanej u góry okna dialogowego **Nowy projekt.**

## <a name="uses-of-the-vsix-project-template"></a>Zastosowania szablonu projektu VSIX

Szablon projektu VSIX ma dwa główne zastosowania:

- Aby wdrożyć szablony projektów, szablony elementów i rozszerzenia.

- Aby zawinąć dane wyjściowe wielu rozszerzeń w jeden pakiet wdrożeniowy.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Pakowanie rozszerzenia w pustym projekcie VSIX

Można spakować istniejące rozszerzenie lub rozszerzenie, które nie ma jeszcze obsługi VSIX, zawijania go w pustym projekcie VSIX. Rozszerzenie, które ma zostać opakowane, musi mieć typ obsługiwany przez [schemat VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Aby spakować rozszerzenie przy użyciu projektu VSIX

1. Tworzenie projektów, które tworzą rozszerzenie.

2. Utwórz projekt VSIX przy użyciu szablonu **projektu VSIX.**

    *Źródło.extension.vsixmanifest* otwiera się w **projektanta manifestu**.

3. Na karcie **Zasoby** wybierz przycisk **Nowy.**

    Zostanie wyświetlone okno dialogowe **Dodawanie nowego zasobu.**

4. Na liście **Typ** wybierz typ rozszerzenia, które chcesz dodać.

5. Aby dodać rozszerzenie lub element zawartości, który znajduje się w bieżącym rozwiązaniu (na przykład szablon elementu lub skompilowany zestaw), wykonaj następujące kroki:

   1. Na liście **Źródło** wybierz pozycję **Projekt w bieżącym rozwiązaniu**.

   2. Na liście **Projekt** wybierz nazwę rozszerzenia.

   3. W polu **Osadzanie w tym folderze** wprowadź nazwę folderu, w którym ma być osadzić zasób, a następnie wybierz przycisk **OK.**

6. Aby dodać rozszerzenie lub element zawartości, który nie jest uwzględniony w bieżącym rozwiązaniu, wykonaj następujące czynności:

   1. W polu **listy Źródło** wybierz pozycję Plik w **systemie plików**.

   2. W polu **Ścieżka** wprowadź pełną ścieżkę do skompilowanego lub skompresowanego pliku rozszerzenia lub użyj przycisku **Przeglądaj,** aby przejść do pliku.

   3. W polu **Osadzanie w tym folderze** wprowadź nazwę folderu, w którym ma być osadzić zasób, a następnie wybierz przycisk **OK.**

7. Jeśli chcesz, aby pakiet zawierał dodatkowe rozszerzenia, dodaj je w ten sam sposób.

8. Skompiluj rozwiązanie.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tworzy plik *vsix,* który zawiera plik manifestu VSIX, plik*xml* [Content_Types] i wszystkie zasoby rozszerzenia dodane do projektu.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu rozszerzenia VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
