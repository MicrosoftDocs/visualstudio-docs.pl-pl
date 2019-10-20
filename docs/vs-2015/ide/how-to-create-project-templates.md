---
title: 'Instrukcje: Tworzenie szablonów projektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f358d5b95349fe99b2a2e01df5158d2c0aa10a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668052"
---
# <a name="how-to-create-project-templates"></a>Porady: tworzenie szablonów projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta procedura umożliwia utworzenie szablonu za pomocą kreatora **eksportu szablonów** , który pakuje szablon w pliku zip. Możesz również utworzyć szablony w formacie pliku VSIX, aby zwiększyć wdrożenie przy użyciu rozszerzenia Kreatora eksportu szablonów lub szablonów zawartych w [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] lub ręcznie tworzyć szablony.

### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Aby utworzyć niestandardowy szablon projektu przy użyciu standardowego Kreatora szablonu eksportu

1. Utwórz projekt.

    > [!NOTE]
    > Używaj tylko prawidłowych znaków identyfikatora podczas nadawania nazwy projektowi, który będzie źródłem szablonu. Szablon wyeksportowany z projektu o nazwie z nieprawidłowymi znakami może spowodować błędy kompilacji w przyszłych projektach opartych na szablonie. Aby uzyskać więcej informacji na temat prawidłowych znaków identyfikatora, zobacz [zadeklarowane nazwy elementów](https://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66).

2. Edytuj projekt, dopóki nie będzie gotowy do eksportowania jako szablon.

3. W razie potrzeby edytuj pliki kodu, aby wskazać, gdzie powinien zostać zamieniony parametr. Aby uzyskać więcej informacji na temat zastępowania parametrów, zobacz [How to: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

4. W menu **plik** kliknij polecenie **Eksportuj szablon**. Zostanie otwarty Kreator **eksportu szablonu** .

5. Kliknij pozycję **szablon projektu**.

6. Jeśli masz więcej niż jeden projekt w bieżącym rozwiązaniu, wybierz projekty, które chcesz wyeksportować do szablonu.

7. Kliknij przycisk **Dalej**.

8. Wybierz ikonę i obraz podglądu dla szablonu. Zostaną one wyświetlone w oknie dialogowym **Nowy projekt** .

9. Wprowadź nazwę i opis szablonu.

10. Kliknij przycisk **Zakończ**. Projekt zostanie wyeksportowany do pliku zip i umieszczony w określonej lokalizacji wyjściowej, a w przypadku wybrania zaimportowany do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

     Jeśli masz zainstalowaną [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)], możesz otoczyć gotowy szablon w pliku. VSIX do wdrożenia przy użyciu szablonu **projektu VSIX** . Aby uzyskać więcej informacji, zobacz [wprowadzenie z szablonem projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Zobacz też
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md) [— instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
