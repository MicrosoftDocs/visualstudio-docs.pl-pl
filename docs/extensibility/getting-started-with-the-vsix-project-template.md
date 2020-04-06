---
title: Wprowadzenie do szablonu projektu VSIX | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711244"
---
# <a name="get-started-with-the-vsix-project-template"></a>Wprowadzenie do szablonu projektu VSIX

Za pomocą szablonu projektu VSIX można utworzyć rozszerzenie lub spakować istniejące rozszerzenie do wdrożenia. Szablon projektu VSIX ma wersje visual basic i visual c# i jest instalowany jako część pakietu SDK programu Visual Studio.

 Szablon projektu VSIX składa się tylko z pliku *source.extension.vsixmanifest,* który zawiera informacje o rozszerzeniu i zasobach, które jest dostarczany.

 Aby znaleźć szablon projektu VSIX, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Wdrażanie niestandardowego szablonu projektu przy użyciu szablonu projektu VSIX

 Poniższe kroki pokazują, jak używać projektu VSIX do pakowania szablonu projektu, który można udostępnić innym deweloperom lub przekazać do galerii programu Visual Studio.

1. Tworzenie szablonu projektu.

    1. Otwórz projekt, z którego chcesz utworzyć szablon. Ten projekt może być dowolnego typu projektu.

    2. W menu **Projekt** kliknij polecenie **Eksportuj szablon**. Wykonaj kroki kreatora.

         Plik *zip* jest tworzony w *pliku %USERPROFILE%\Moje dokumenty\Visual Studio {version}\Moje wyeksportowane szablony\\*.

2. Utwórz pusty projekt VSIX.

     Wybierz **pozycję Plik** > **nowy** > **projekt**. W polu wyszukiwania wpisz "vsix" i wybierz wersję programu **VSIX Project** **w języku C#** lub **Visual Basic.**

3. Dodaj plik *zip* do projektu. Ustaw jego **polecenie Kopiuj na katalog wyjściowy** na `Copy Always`.

4. W **Eksploratorze rozwiązań**kliknij dwukrotnie plik *source.extension.vsixmanifest,* aby otworzyć go w **projektancie manifestu VSIX,** a następnie wprowadzać następujące zmiany:

    - Ustaw pole **Nazwa produktu** na Mój **szablon projektu**.

    - Ustaw pole **Identyfikator produktu** na **MyProjectTemplate - 1**.

    - Ustaw pole **Autor** na **Fabrikam**.

    - Ustaw pole **Opis** na **Szablon mojego projektu**.

    - W sekcji **Zasoby** dodaj typ **microsoft.VisualStudio.ProjectTemplate** i ustaw jego ścieżkę do nazwy pliku *zip.*

5. Zapisz i zamknij plik *source.extension.vsixmanifest.*

6. Skompiluj projekt.

7. W katalogu wyjściowym kliknij dwukrotnie plik *vsix.*

8. Zostanie wyświetlenie okna komunikatu **instalatora VSIX.** Postępuj zgodnie z instrukcjami, aby zainstalować rozszerzenie.

9. Zamknij program Visual Studio, a następnie otwórz go ponownie.

::: moniker range="vs-2017"

10. Wybierz **pozycję Rozszerzenia i aktualizacje** (w menu **Narzędzia)** i wybierz kategorię **Szablony.** Jednym z dostępnych rozszerzeń powinien być **mój szablon projektu**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Wybierz **pozycję Zarządzaj rozszerzeniami** (w menu **Rozszerzenia)** i wybierz kategorię **Szablony.** Jednym z dostępnych rozszerzeń powinien być **mój szablon projektu**.

::: moniker-end

11. Nowy szablon projektu pojawi się w oknie dialogowym **Nowy projekt** w tym samym miejscu co oryginalny szablon projektu. Jeśli na przykład utworzono szablon o nazwie **Konsola VB** z aplikacji konsoli Języka Visual Basic, **konsola VB** pojawi się w tym samym okienku co szablon **aplikacji konsoli** Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Aby określić lokalizację szablonu w oknie dialogowym Nowy projekt

1. Foldery szablonów znajdują się w katalogach *{Visual Studio Installation Path}\Common7\IDE\ProjectTemplates* i *{Visual Studio Installation Path}\Common7\IDE\ItemTemplates.* Nazwy sekcji najwyższego poziomu w oknie dialogowym **Nowy projekt** nie są dokładnie zgodne z nazwami folderów szablonów. Jeśli się różnią, użyj nazwy folderu szablonu.

    Zmień rozszerzenie pliku *vsix* na *.zip*, a następnie otwórz plik.

2. Utwórz nowy folder o takiej samej nazwie jak sekcja okna dialogowego **Nowy projekt,** w których powinien pojawić się szablon.

3. Jeśli szablon ma być wyświetlany w podsekcji, utwórz podfolder o tej samej nazwie.

4. Przenieś *plik* zip szablonu do nowego folderu.

5. Zmień rozszerzenie *.zip* na *.vsix*.

6. Otwórz manifest VSIX.

7. W manifeście VSIX zaktualizuj ścieżkę **zasobu** szablonu, tak aby wszechłała do katalogu głównego drzewa katalogów zawierającego plik szablonu. Na przykład, jeśli szablon znajduje się w *folderze \CSharp\Windows,* odwołanie powinno wskazywać *\CSharp*.
