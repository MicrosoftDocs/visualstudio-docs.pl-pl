---
title: Otwieranie i zapisywanie elementów projektu | Microsoft Docs
description: Poznaj różne podejścia do otwierania i zapisywania plików dla nowego typu projektu w środowisku IDE programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ff3c76294ce99fa5eeb7bf311307e54f5d0e6cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063074"
---
# <a name="opening-and-saving-project-items"></a>Otwieranie i zapisywanie elementów projektu
Po dodaniu nowego typu projektu należy zarządzać otwieraniem i zapisywaniem plików projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE). W poniższych tematach omówiono różne podejścia do otwierania i zapisywania plików.

## <a name="in-this-section"></a>W tej sekcji
- [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Zawiera objaśnienie krok po kroku dotyczące sposobu, w jaki środowisko IDE obsługuje polecenie **Otwórz plik** i rolę projektów w odpowiedzi na to polecenie.

- [Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Zawiera szczegółowe objaśnienie krok po kroku dotyczące sposobu, w jaki środowisko IDE obsługuje polecenie **Otwórz za pomocą** , monitując o otwarcie pliku, który ma kilka wybranych edytorów standardowych.

- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)

 Zawiera instrukcje krok po kroku dotyczące określania, że pliki określonego typu w projekcie powinny być otwierane za pomocą edytora specyficznego dla projektu.

- [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)

 Zawiera instrukcje krok po kroku dotyczące sposobu włączania środowiska IDE do otwierania standardowego edytora dla plików w typie projektu.

- [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)

 Zawiera instrukcje krok po kroku, aby otworzyć Edytor specyficzny dla projektu dla otwartego pliku.

- [Zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md)

 Zawiera szczegółowy opis sposobu, w jaki środowisko IDE obsługuje **Zapisywanie**, **Zapisywanie jako** i **zapisywanie wszystkich** poleceń dla dokumentu otwartego w standardowym edytorze.

- [Zapisywanie niestandardowego dokumentu](../../extensibility/internals/saving-a-custom-document.md)

 Zawiera diagram i szczegółowe wyjaśnienie, jak środowisko IDE obsługuje **Zapisywanie**, **Zapisywanie jako** i **zapisywanie wszystkich** poleceń dla dokumentów otwartych w edytorze niestandardowym.

- [Określanie, który edytor służy do otwierania pliku w projekcie](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 W tym artykule omówiono proces, w którym IDE następuje wybranie odpowiedniego edytora lub projektanta pliku.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md)

 Wyświetla cztery typy edytorów, które mogą być obsługiwane przez środowisko IDE i zawiera opisy poszczególnych edytorów.

- [Typy projektów](../../extensibility/internals/project-types.md)

 W tym artykule omówiono sposób, w jaki projekty kontrolują sposób, w jaki kod jest kompilowany i skompilowany, jak edytory są otwierane oraz jak są formatowane elementy projektu.
