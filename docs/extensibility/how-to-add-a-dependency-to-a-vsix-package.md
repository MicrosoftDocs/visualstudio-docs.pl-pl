---
title: 'Jak: Dodawanie zależności do pakietu VSIX | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711076"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Jak: Dodawanie zależności do pakietu VSIX

Można skonfigurować wdrożenie pakietu VSIX, który instaluje wszystkie zależności, które nie są jeszcze obecne na komputerze docelowym. Aby to osiągnąć, należy uwzględnić zależności VSIX do pliku *source.extension.vsixmanifest.*

## <a name="to-add-a-dependency"></a>Aby dodać zależność

1. Otwórz plik *source.extension.vsixmanifest* w widoku **Projekt.** Przejdź do karty **Zależności** i kliknij pozycję **Nowy**.

2. Aby dodać zainstalowane rozszerzenie: w oknie dialogowym **Dodawanie nowych zależności** wybierz pozycję Zainstalowane **rozszerzenie,** a następnie wybierz **pozycję Nazwa**wybierz rozszerzenie na liście.

3. Aby dodać kolejny nieużywany system VSIX: w oknie dialogowym **Dodawanie nowych zależności** wybierz pozycję Plik w systemie **plików,** a następnie użyj przycisku **Przeglądaj,** aby wybrać vsix.

## <a name="require-a-specific-visual-studio-release"></a>Wymagaj określonej wersji programu Visual Studio

Jeśli rozszerzenie wymaga określonej wersji programu Visual Studio 2017, na przykład zależy to od funkcji wydanej w wersji 15.3, można określić numer kompilacji w programie VSIX **InstallationTarget**. Na przykład wersja 15.3 ma numer kompilacji "15.0.26730.3". Możesz zobaczyć mapowanie wersji do tworzenia numerów [tutaj](../install/visual-studio-build-numbers-and-release-dates.md). Należy pamiętać, że użycie numeru wydania "15.3" nie będzie działać poprawnie.

Jeśli rozszerzenie wymaga wersji 15.3 lub **nowszej, należy zadeklarować wersję InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller wykryje wcześniejsze wersje programu Visual Studio i poinformuje użytkownika, że wymagana jest późniejsza aktualizacja.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu rozszerzenia VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Przygotowywanie rozszerzeń do wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
