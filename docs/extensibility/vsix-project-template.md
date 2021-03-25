---
title: Szablon projektu VSIX | Microsoft Docs
description: Dowiedz się, jak używać szablonu projektu VSIX do zawijania rozszerzeń programu Visual Studio w projekcie VSIX, a następnie publikować pakiet na Visual Studio Marketplace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8f8e5e9f9a5a21600aa894ee8b7f6c3730bc1fc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062268"
---
# <a name="vsix-project-template"></a>Szablon projektu VSIX

Możesz użyć szablonu projektu VSIX, aby otoczyć co najmniej jedno rozszerzenie programu Visual Studio w projekcie VSIX, a następnie opublikować pakiet w witrynie sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

 Wdrożenie VSIX obsługuje pakietów VSPackage, zestawy, składniki MEF, szablony projektów, szablony elementów, formanty przybornika i niestandardowe typy rozszerzeń.

> [!NOTE]
> Aby można było korzystać z projektów VSIX, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji na temat zestawu Visual Studio SDK, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Gdzie znaleźć szablon projektu VSIX

Szablon projektu VSIX jest dostępny w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".  Istnieje zarówno wersja języka C#, jak i Visual Basic.

> [!TIP]
> Upewnij się, że w polu listy rozwijanej w górnej części okna dialogowego **Nowy projekt** określono .NET Framework 4,5 lub wyższą.

## <a name="uses-of-the-vsix-project-template"></a>Użycie szablonu projektu VSIX

Szablon projektu VSIX ma dwa główne zastosowania:

- Do wdrażania szablonów projektu, szablonów elementów i rozszerzeń.

- Aby otoczyć dane wyjściowe wielu rozszerzeń w jednym pakiecie wdrożeniowym.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Pakowanie rozszerzenia w pustym projekcie VSIX

Można spakować istniejące rozszerzenie lub rozszerzenie, które nie ma jeszcze obsługi VSIX, zawijając je w pustym projekcie VSIX. Rozszerzenie, które ma być opakowane, musi być typu, który jest obsługiwany przez [schemat VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Aby spakować rozszerzenie przy użyciu projektu VSIX

1. Kompiluj projekty wchodzące w skład rozszerzenia.

2. Utwórz projekt VSIX przy użyciu szablonu **projektu VSIX** .

    Plik *source. Extension. vsixmanifest* zostanie otwarty w **Projektancie manifestów**.

3. Na karcie **zasoby** wybierz przycisk **Nowy** .

    Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

4. Z listy **Typ** wybierz typ rozszerzenia do dodania.

5. Aby dodać rozszerzenie lub element zawartości, który znajduje się w bieżącym rozwiązaniu (na przykład szablon elementu lub skompilowany zestaw), wykonaj następujące czynności:

   1. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

   2. Na liście **projekt** wybierz nazwę rozszerzenia.

   3. W polu **Osadź w tym folderze** wprowadź nazwę folderu, w którym ma zostać osadzony element zawartości, a następnie wybierz przycisk **OK** .

6. Aby dodać rozszerzenie lub element zawartości, który nie jest uwzględniony w bieżącym rozwiązaniu, wykonaj następujące czynności:

   1. W polu listy **Źródło** wybierz pozycję **plik w systemie plików**.

   2. W polu **ścieżka** wprowadź pełną ścieżkę do skompilowanego lub skompresowanego pliku rozszerzenia lub użyj przycisku **Przeglądaj** , aby przejść do pliku.

   3. W polu **Osadź w tym folderze** wprowadź nazwę folderu, w którym ma zostać osadzony element zawartości, a następnie wybierz przycisk **OK** .

7. Jeśli chcesz, aby pakiet zawierał dodatkowe rozszerzenia, Dodaj je w taki sam sposób.

8. Skompiluj rozwiązanie.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kompiluje plik *. vsix* zawierający plik manifestu VSIX, plik [Content_Types]*. XML* i wszystkie zasoby rozszerzenia dodane do projektu.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja schematu rozszerzenia VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
