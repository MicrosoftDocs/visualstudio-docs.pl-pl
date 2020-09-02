---
title: Otwieranie i zapisywanie elementów projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c406e66b1008f0bb2aad95a427e1329d4269f1f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158066"
---
# <a name="opening-and-saving-project-items"></a>Otwieranie i zapisywanie elementów projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po dodaniu nowego typu projektu należy zarządzać otwieraniem i zapisywaniem plików projektów w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE). W poniższych tematach omówiono różne podejścia do otwierania i zapisywania plików.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Zawiera objaśnienie krok po kroku dotyczące sposobu, w jaki środowisko IDE obsługuje polecenie **Otwórz plik** i rolę projektów w odpowiedzi na to polecenie.  
  
 [Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Zawiera szczegółowe objaśnienie krok po kroku dotyczące sposobu, w jaki środowisko IDE obsługuje polecenie **Otwórz za pomocą** , monitując o otwarcie pliku, który ma kilka wybranych edytorów standardowych.  
  
 [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Zawiera instrukcje krok po kroku dotyczące określania, że pliki określonego typu w projekcie powinny być otwierane za pomocą edytora specyficznego dla projektu.  
  
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)  
 Zawiera instrukcje krok po kroku dotyczące sposobu włączania środowiska IDE do otwierania standardowego edytora dla plików w typie projektu.  
  
 [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Zawiera instrukcje krok po kroku, aby otworzyć Edytor specyficzny dla projektu dla otwartego pliku.  
  
 [Zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md)  
 Zawiera szczegółowy opis sposobu, w jaki środowisko IDE obsługuje **Zapisywanie**, **Zapisywanie jako**i **zapisywanie wszystkich** poleceń dla dokumentu otwartego w standardowym edytorze.  
  
 [Zapisywanie niestandardowego dokumentu](../../extensibility/internals/saving-a-custom-document.md)  
 Zawiera diagram i szczegółowe wyjaśnienie, jak środowisko IDE obsługuje **Zapisywanie**, **Zapisywanie jako**i **zapisywanie wszystkich** poleceń dla dokumentów otwartych w edytorze niestandardowym.  
  
 [Określanie, który edytor służy do otwierania pliku w projekcie](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 W tym artykule omówiono proces, w którym IDE następuje wybranie odpowiedniego edytora lub projektanta pliku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md)  
 Wyświetla cztery typy edytorów, które mogą być obsługiwane przez środowisko IDE i zawiera opisy poszczególnych edytorów.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono sposób, w jaki projekty kontrolują sposób, w jaki kod jest kompilowany i skompilowany, jak edytory są otwierane oraz jak są formatowane elementy projektu.
