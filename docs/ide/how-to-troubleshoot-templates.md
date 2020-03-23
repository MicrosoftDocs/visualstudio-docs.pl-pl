---
title: Rozwiązywanie problemów z ładowaniem szablonu projektu i szablonu elementu
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bef6a460f1a59823930597565b955b591ab48a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591388"
---
# <a name="how-to-troubleshoot-templates"></a>Jak: Rozwiązywanie problemów z szablonami

Jeśli szablon nie można załadować w środowisku programistycznym, istnieje kilka sposobów, aby zlokalizować problem.

## <a name="validate-the-vstemplate-file"></a>Sprawdzanie poprawności pliku vstemplate

::: moniker range="vs-2017"

Jeśli plik *vstemplate* w szablonie nie jest zgodny ze schematem szablonu programu Visual Studio, szablon może nie być wyświetlany w oknie dialogowym **Nowy projekt.**

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli plik *vstemplate* w szablonie nie jest zgodny ze schematem szablonu programu Visual Studio, szablon może nie być wyświetlany w oknie dialogowym, w którym tworzysz nowe projekty.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Aby sprawdzić poprawność pliku vstemplate

1. Znajdź plik *zip* zawierający szablon.

1. Wyodrębnij plik *.zip.*

1. W menu **Plik** w programie Visual Studio wybierz polecenie **Otwórz** > **plik**.

1. Wybierz plik *vstemplate* dla szablonu i wybierz pozycję **Otwórz**.

1. Sprawdź, czy kod XML pliku *vstemplate* jest zgodny ze schematem szablonu. Aby uzyskać więcej informacji na temat schematu *vstemplate,* zobacz [Odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Aby uzyskać obsługę technologii IntelliSense podczas tworzenia pliku *vstemplate,* dodaj `xmlns` atrybut do `VSTemplate` elementu i przypisz mu wartość `http://schemas.microsoft.com/developer/vstemplate/2005`.

1. Zapisz i zamknij plik *vstemplate.*

1. Wybierz pliki zawarte w szablonie, kliknij prawym przyciskiem myszy i wybierz polecenie **Wyślij do** > **folderu Skompresowanego (spakowane).** Wybrane pliki zostaną skompresowane do pliku *zip.*

1. Umieść nowy plik *zip* w tym samym katalogu co stary plik *zip.*

1. Usuń wyodrębnione pliki szablonów i stary plik *.zip* szablonu.

## <a name="enable-diagnostic-logging"></a>Włączanie rejestrowania diagnostycznego

Rejestrowanie diagnostyczne do odnajdowania szablonów można włączyć, wykonując czynności opisane w programie [Rozwiązywanie problemów z odnajdowaniem szablonów (rozszerzalność).](../extensibility/troubleshooting-template-discovery.md)

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z odnajdywaniam szablonów (rozszerzalność)](../extensibility/troubleshooting-template-discovery.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
