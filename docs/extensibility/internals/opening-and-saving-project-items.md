---
title: Otwieranie i zapisywanie elementów projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a7c9cae59bc5a02dcca53afb66c234012e6713
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918684"
---
# <a name="opening-and-saving-project-items"></a>Otwieranie i zapisywanie elementów projektu
Po dodaniu nowych typów projektów, należy zarządzać otwieranie i zapisywanie plików projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). W poniższych tematach omówiono różne podejścia do otwierania i zapisywania plików.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Zawiera szczegółowe omówienie sposobu obsługi środowiska IDE **Otwórz plik** polecenia i rolę projektów w odpowiedzi na to polecenie.  
  
 [Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Zapewnia szczegółowe, krok po kroku wyjaśnienie sposobu obsługi IDE **Otwórz za pomocą** polecenie otwarcia pliku, który ma kilka wybór standardowych edytorów monitowania.  
  
 [Instrukcje: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Instrukcje krok po kroku do określania, że pliki określonego typu projektu powinien zostać otwarty przy użyciu edytora specyficznych dla projektu.  
  
 [Instrukcje: Otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)  
 Instrukcje krok po kroku do określania sposobu włączania IDE otworzyć Edytor standardowy dla plików typu projektu.  
  
 [Instrukcje: Otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Instrukcje krok po kroku można otworzyć edytora specyficznych dla projektu, dla otwartego pliku.  
  
 [Zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md)  
 Zawiera szczegółowy opis sposobu obsługi IDE **Zapisz**, **Zapisz jako**, i **Zapisz wszystko** poleceń dokument otwarty w edytora standardowego.  
  
 [Zapisywanie niestandardowego dokumentu](../../extensibility/internals/saving-a-custom-document.md)  
 Zawiera diagram i szczegółowy opis sposobu obsługi IDE **Zapisz**, **Zapisz jako**, i **Zapisz wszystko** poleceń dla dokumentów otwarty w edytorze niestandardowym.  
  
 [Określanie, który edytor służy do otwierania pliku w projekcie](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 W tym artykule omówiono proces, znajdujący się IDE wybierz odpowiedniego edytora lub projektanta dla pliku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md)  
 Zawiera cztery typy edytory, IDE może obsługiwać i zawiera opisy każdej edytora.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono, jak projekty kontrolować sposób, że kod jest kompilowania i tworzenia, jak edytory są otwarte i jak elementy projektu są sformatowane.