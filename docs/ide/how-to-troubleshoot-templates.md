---
title: Rozwiązywanie problemów z szablonami projektów i szablonami elementów
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ddb164dbd43d1d2276fce66641ba6e647b49143e
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045714"
---
# <a name="how-to-troubleshoot-templates"></a>Instrukcje: Rozwiązywanie problemów z szablonami

Jeśli szablon nie zostanie załadowany w środowisku deweloperskim, istnieje kilka sposobów zlokalizowania problemu.

## <a name="validate-the-vstemplate-file"></a>Sprawdź poprawność pliku vstemplate

::: moniker range="vs-2017"

Jeśli plik *vstemplate* w szablonie nie jest zgodny ze schematem szablonu programu Visual Studio, szablon może nie pojawić się w oknie dialogowym **Nowy projekt** .

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli plik *vstemplate* w szablonie nie jest zgodny ze schematem szablonu programu Visual Studio, szablon może nie być wyświetlany w oknie dialogowym, w którym tworzysz nowe projekty.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Aby sprawdzić poprawność pliku vstemplate

1. Znajdź plik *zip* , który zawiera szablon.

1. Wyodrębnij plik *zip* .

1. W menu **plik** w programie Visual Studio wybierz polecenie **Otwórz**  >  **plik** .

1. Wybierz plik *vstemplate* szablonu i wybierz polecenie **Otwórz** .

1. Sprawdź, czy plik XML pliku *vstemplate* jest zgodny ze schematem szablonu. Aby uzyskać więcej informacji na temat schematu *vstemplate* , zobacz [Dokumentacja schematu szablonu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Aby uzyskać pomoc techniczną IntelliSense podczas tworzenia pliku *vstemplate* , Dodaj `xmlns` atrybut do `VSTemplate` elementu i przypisz mu wartość `http://schemas.microsoft.com/developer/vstemplate/2005` .

1. Zapisz i zamknij plik *vstemplate* .

1. Wybierz pliki dołączone do szablonu, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Wyślij do**  >  **folderu skompresowanego (spakowanego)** . Wybrane pliki są kompresowane do pliku *zip* .

1. Umieść nowy plik *zip* w tym samym katalogu, w którym znajduje się stary plik *. zip* .

1. Usuń wyodrębnione pliki szablonów i stary plik template *. zip* .

## <a name="enable-diagnostic-logging"></a>Włączanie rejestrowania diagnostycznego

Rejestrowanie diagnostyczne można włączyć dla odnajdywania szablonów, wykonując czynności opisane w temacie [Rozwiązywanie problemów z odnajdywaniem szablonów (rozszerzalnością)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z odnajdywaniem szablonów (rozszerzalność)](../extensibility/troubleshooting-template-discovery.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Dokumentacja schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
