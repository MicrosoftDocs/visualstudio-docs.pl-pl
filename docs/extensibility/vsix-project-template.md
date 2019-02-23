---
title: Szablon projektu VSIX | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92db48197791bab4b5f364ee6d2cd0e948e2a5f7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684588"
---
# <a name="vsix-project-template"></a>VSIX project template
Można użyć szablonu projektu VSIX do opakowania jedno lub więcej rozszerzeń programu Visual Studio w projekcie VSIX, a następnie opublikować pakiet na [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witryny sieci Web.

 Wdrożenie VSIX obsługuje pakietów VSPackage, zestawy, składniki MEF, szablony projektów, szablonów elementów, kontrolki przybornika i typy rozszerzeń niestandardowych.

> [!NOTE]
>  Aby korzystać z projektów VSIX, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji na temat zestawu SDK programu Visual Studio, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Gdzie można znaleźć szablonu projektu VSIX
 Szablon projektu VSIX jest dostępny w **nowy projekt** okno dialogowe. Rozwiń **języka Visual Basic** węzła lub **Visual C#** węzła, a następnie wybierz **rozszerzalności**.

> [!TIP]
>  Upewnij się, że program .NET Framework 4.5 lub nowszy, jest określony w polu listy rozwijanej w górnej części **nowy projekt** okno dialogowe.

## <a name="uses-of-the-vsix-project-template"></a>Używa szablonu projektu VSIX
 Szablon projektu VSIX ma dwa podstawowe zastosowania:

- Aby wdrożyć szablony projektów, szablonów elementów i inne rozszerzenia, które nie zostały jeszcze obsługi VSIX.

- Aby opakować dane wyjściowe z wielu rozszerzeń w pakiecie jedno wdrożenie.

  Nie trzeba użyć szablonu projektu VSIX do wdrożenia pakietów VSPackage lub innych rodzajów rozszerzenia, które mają już VSIX obsługi.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Pakowanie rozszerzenia w pusty projekt VSIX
 Można spakować istniejące rozszerzenie lub rozszerzenie, które nie ma jeszcze VSIX obsługi, opakowując go w projekcie VSIX jest pusty. Rozszerzenia w celu jej opakowania musi być typu, który jest obsługiwany przez [schematu VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Aby utworzyć pakiet rozszerzenia za pomocą projektu VSIX

1. Twórz projekty, które składają się na Twoje rozszerzenie.

2. Utwórz projekt VSIX przy użyciu **projekt VSIX** szablonu.

    *Source.Extension.vsixmanifest* zostanie otwarty w **Manifest Designer**.

3. Na **zasoby** kartę, wybrać **New** przycisku.

    **Dodaj nowy zasób** pojawi się okno dialogowe.

4. W **typu** listy, wybierz typ rozszerzenie do dodania.

5. Aby dodać rozszerzenie lub zawartości elementu, który znajduje się w bieżącym rozwiązaniu (na przykład szablon elementu lub skompilowanego zestawu), wykonaj następujące czynności:

   1.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

   2.  W **projektu** , wybierz nazwę rozszerzenia.

   3.  W **osadzania w tym folderze** wprowadź nazwę folderu, w której chcesz osadzić elementu zawartości, a następnie wybierz **OK** przycisku.

6. Aby dodać rozszerzenie lub element zawartości, który nie znajduje się w bieżącym rozwiązaniu, wykonaj następujące czynności:

   1.  W **źródła** pola listy, wybierz **plików w systemie plików**.

   2.  W **ścieżki** pole, wprowadź pełną ścieżkę do pliku rozszerzenie skompilowany lub skompresowany lub użyj **Przeglądaj** przycisk, aby przejść do pliku.

   3.  W **osadzania w tym folderze** wprowadź nazwę folderu, w której chcesz osadzić elementu zawartości, a następnie wybierz **OK** przycisku.

7. Jeśli chcesz, aby do pakietu, aby uwzględnić dodatkowe rozszerzenia, należy je dodać w taki sam sposób.

8. Skompiluj rozwiązanie.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kompilacje *.vsix* pliku, który zawiera plik manifestu VSIX [Content_Types]*.xml* pliku i wszystkie zasoby rozszerzenia, które zostały dodane do projektu.

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu 2.0 rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)