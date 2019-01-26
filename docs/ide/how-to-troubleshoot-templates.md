---
title: Rozwiązywanie problemów z szablonu projektu i szablon elementu ładowania
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cc8507388e4ef9311aeb5345e5f91bd43340f5d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027415"
---
# <a name="how-to-troubleshoot-templates"></a>Instrukcje: Rozwiązywanie problemów z szablonami

Jeśli szablon nie są ładowane w środowisku deweloperskim, istnieją zlokalizowania problemu na kilka sposobów.

## <a name="validate-the-vstemplate-file"></a>Sprawdź poprawność pliku vstemplate

Jeśli *vstemplate* pliku w szablonie nie stosować się do schematu szablonu Visual Studio, szablon nie może występować w **nowy projekt** okno dialogowe.

### <a name="to-validate-the-vstemplate-file"></a>Aby sprawdzić poprawność pliku vstemplate

1. Znajdź *zip* pliku, który zawiera szablon.

1. Wyodrębnij *zip* pliku.

1. Na **pliku** menu w programie Visual Studio, wybierz opcję **Otwórz** > **pliku**.

1. Wybierz *vstemplate* pliku szablonu, a następnie wybierz **Otwórz**.

1. Upewnij się, że plik XML *vstemplate* plików jest zgodna ze schematem szablonu. Aby uzyskać więcej informacji na temat *vstemplate* schematu, zobacz [odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Aby uzyskać obsługę technologii IntelliSense podczas tworzenia *vstemplate* Dodaj `xmlns` atrybutu `VSTemplate` element i przypisz jej wartość http://schemas.microsoft.com/developer/vstemplate/2005.

1. Zapisz i Zamknij *vstemplate* pliku.

1. Wybierz pliki zawarte w szablonie, kliknij prawym przyciskiem myszy, a wybierz **wysyłać** > **skompresowany folder (zip)**. Wybrane pliki są kompresowane do *zip* pliku.

1. Umieść nową *zip* pliku w tym samym katalogu co stary *zip* pliku.

1. Usuń pliki szablonów wyodrębniony i starego szablonu *zip* pliku.

## <a name="enable-diagnostic-logging"></a>Włączanie rejestrowania diagnostycznego

Można włączyć rejestrowanie diagnostyczne dla odnajdywania szablonów, wykonując kroki opisane w [odnajdywania szablonów rozwiązywania problemów (rozszerzalność)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów z odnajdywania szablonu (rozszerzalność)](../extensibility/troubleshooting-template-discovery.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)