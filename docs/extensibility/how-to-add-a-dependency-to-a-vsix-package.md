---
title: 'Instrukcje: Dodawanie zależności do pakietu VSIX | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ce21c10f1a64bf8edad9181d66b83291d0405c4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902483"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Instrukcje: Dodawanie zależności do pakietu VSIX

Można skonfigurować wdrożenie pakietu VSIX, które instaluje wszystkie zależności, które nie są już obecne na komputerze docelowym. Aby to osiągnąć, należy uwzględnić zależności VSIX *source.extension.vsixmanifest* pliku.

## <a name="to-add-a-dependency"></a>Aby dodać zależności

1. Otwórz *source.extension.vsixmanifest* w pliku **projektowania** widoku. Przejdź do **zależności** kartę, a następnie kliknij przycisk **New**.

2. Aby dodać zainstalowane rozszerzenie: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **zainstalowane rozszerzenie** a następnie w **nazwa**, zaznacz rozszerzenie, na liście.

3. Aby dodać inny VSIX, który nie jest zainstalowany: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **plików w systemie plików** , a następnie użyj **Przeglądaj** przycisk, aby wybrać VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Wymagaj określonej wersji programu Visual Studio

Jeśli rozszerzenie wymaga określonej wersji programu Visual Studio 2017, na przykład, zależy od funkcją udostępnioną w 15.3, można określić numer kompilacji w VSIX użytkownika **InstallationTarget**. Na przykład wersja 15.3 ma numer kompilacji "15.0.26730.3". Możesz zobaczyć mapowanie wersji numery kompilacji [tutaj](../install/visual-studio-build-numbers-and-release-dates.md). Należy pamiętać, że za pomocą numeru wersji "15.3" nie będą działać poprawnie.

Jeśli Twojego rozszerzenia wymaga 15.3 lub nowszej, może zadeklarować **wersji InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Instalator VSIX wykryje wcześniejszych wersji programu Visual Studio i informować użytkownika, że nowsza aktualizacja jest wymagana.


## <a name="see-also"></a>Zobacz także

 [Odwołanie do schematu 1.0 rozszerzenia VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
