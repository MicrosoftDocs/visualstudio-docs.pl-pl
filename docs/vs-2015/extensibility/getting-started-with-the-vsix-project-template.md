---
title: Wprowadzenie z szablonem projektu VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc3f461c9e7dbdea1fd8481594292a0a247d2173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204298"
---
# <a name="getting-started-with-the-vsix-project-template"></a>Wprowadzenie do szablonu projektu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć szablonu projektu VSIX, aby utworzyć rozszerzenie lub spakować istniejące rozszerzenie do wdrożenia. Szablon projektu VSIX ma wersje Visual Basic i Visual C# i jest instalowany jako część zestawu Visual Studio SDK.  
  
 Szablon projektu VSIX składa się tylko z pliku source. Extension. vsixmanifest, który zawiera informacje o rozszerzeniu i zasobach, które dostarcza.  
  
 Aby znaleźć szablon projektu VSIX, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Wdrażanie niestandardowego szablonu projektu przy użyciu szablonu projektu VSIX  
 W poniższych krokach pokazano, jak za pomocą projektu VSIX spakować szablon projektu, który można udostępnić innym deweloperom lub przekazać do galerii programu Visual Studio.  
  
1. Utwórz szablon projektu.  
  
    1. Otwórz projekt, z którego ma zostać utworzony szablon. Ten projekt może być dowolnego typu projektu.  
  
    2. W menu **plik** kliknij polecenie **Eksportuj szablon**. Wykonaj kroki kreatora.  
  
         Plik. zip jest tworzony w programie%USERPROFILE%\My Documents\Visual Studio *\<version>* \Moje wyeksportowane szablony \\ .  
  
2. Utwórz pusty projekt VSIX.  
  
     W menu **plik** kliknij pozycję **Nowy** , a następnie kliknij pozycję **projekt**. Wybierz pozycję **Visual Basic** lub **Visual C#**. W obszarze wybrany węzeł wybierz pozycję **rozszerzalność**, a następnie wybierz pozycję **Projekt VSIX**.  
  
3. Dodaj plik. zip do projektu. Ustaw właściwość **Kopiuj do katalogu wyjściowego** na `Copy Always` .  
  
4. W **Eksplorator rozwiązań**kliknij dwukrotnie `source.extension.vsixmanifest` plik, aby otworzyć go w **projektancie manifestu VSIX**, a następnie wprowadź następujące zmiany:  
  
    - W polu **Nazwa produktu** ustaw wartość **mój szablon projektu**.  
  
    - Ustaw wartość pola **Identyfikator produktu** na **MyProjectTemplate-1**.  
  
    - Ustaw pole **autor** na **Fabrikam**.  
  
    - Ustaw pole **Opis** na **mój szablon projektu**.  
  
    - W sekcji **elementy zawartości** Dodaj typ **Microsoft. VisualStudio. ProjectTemplate** i ustaw jego ścieżkę na nazwę pliku. zip.  
  
5. Zapisz i zamknij plik source. Extension. vsixmanifest.  
  
6. Skompiluj projekt.  
  
7. W katalogu wyjściowym kliknij dwukrotnie plik. VSIX.  
  
8. Zostanie wyświetlone okno komunikatu **Instalatora VSIX** . Postępuj zgodnie z instrukcjami, aby zainstalować rozszerzenie.  
  
9. Zamknij program Visual Studio, a następnie otwórz go ponownie.  
  
10. Wybierz pozycję **rozszerzenia i aktualizacje** (w menu **Narzędzia** ) i wybierz kategorię **Szablony** . Jednym z dostępnych rozszerzeń powinien być **mój szablon projektu**.  
  
11. Nowy szablon projektu pojawi się w oknie dialogowym **Nowy projekt** w tym samym miejscu co oryginalny szablon projektu. Jeśli na przykład utworzono szablon o nazwie **konsola VB** z poziomu aplikacji konsolowej Visual Basic, **konsola VB** zostanie wyświetlona w tym samym okienku co szablon **aplikacji konsolowej** Visual Basic.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Aby określić lokalizację szablonu w oknie dialogowym Nowy projekt  
  
1. Foldery szablonów znajdują się w *ścieżce instalacji programu Visual Studio*\Common7\IDE\ProjectTemplates i *ścieżce instalacji programu Visual Studio*\Common7\IDE\ItemTemplates. Nazwy sekcji najwyższego poziomu w oknie dialogowym Nowy projekt nie są dokładnie zgodne z nazwami folderów szablonów. Gdzie się różnią, użyj nazwy folderu szablonów.  
  
     Zmień rozszerzenie pliku VSIX na zip, a następnie otwórz plik.  
  
2. Utwórz nowy folder o takiej samej nazwie jak sekcja okna dialogowego Nowy projekt, w którym powinien się znajdować szablon.  
  
3. Jeśli szablon jest wyświetlany w podsekcji, utwórz podfolder o tej samej nazwie.  
  
4. Przenieś plik Template. zip do nowego folderu.  
  
5. Zmień rozszerzenie zip na. VSIX.  
  
6. Otwórz manifest VSIX.  
  
7. W manifeście VSIX zaktualizuj ścieżkę **zasobu** szablonu, tak aby wskazywała katalog główny drzewa katalogów zawierającego plik szablonu. Na przykład jeśli szablon znajduje się w \CSharp\Windows, odwołanie powinno wskazywać na \CSharp.
