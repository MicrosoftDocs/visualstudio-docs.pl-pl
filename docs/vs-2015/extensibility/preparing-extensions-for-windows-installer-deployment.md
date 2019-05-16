---
title: Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694593"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą pakietu Instalatora Windows (MSI) nie można wdrożyć pakiet VSIX. Jednak można wyodrębnić zawartości pakietu VSIX do wdrożenia MSI. W tym dokumencie pokazano, jak przygotować projektu, którego domyślne dane wyjściowe to pakiet VSIX do włączenia do projektu Instalatora.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Przygotowanie projektu rozszerzenia dla wdrożenia Instalatora Windows  
 Te kroki można wykonać na nowe projekty rozszerzenie, przed dodaniem do projektu Instalatora.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Aby przygotować projekt rozszerzenia dla wdrożenia Instalatora Windows  
  
1. Tworzenie pakietu VSPackage, składnik MEF, zakończeń edytora lub innych typów projektów rozszerzalności, która zawiera manifestu VSIX.  
  
2. Otwórz manifestu VSIX w edytorze kodu.  
  
3. Element InstalledByMsi manifestu VSIX, aby ustawić `true`. Aby uzyskać więcej informacji na temat manifestu VSIX, zobacz [VSIX rozszerzenia schematu 2.0 Reference](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Zapobiega to próby instalacji składnika Instalator VSIX.  
  
4. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i kliknij przycisk **właściwości**.  
  
5. Wybierz **VSIX** kartę.  
  
6. Sprawdź pole o nazwie **VSIX kopiowania zawartości do następującej lokalizacji** i wpisz ścieżkę, do której pliki przejmą projektu Instalatora.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Wypakowywanie plików z istniejącego pakietu VSIX  
 Wykonaj następujące kroki, aby dodać zawartość istniejącego pakietu VSIX do projektu Instalatora, gdy nie masz pliki źródłowe.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Aby wyodrębnić pliki z istniejącego pakietu VSIX  
  
1. Zmień nazwę. Plik VSIX, zawierający rozszerzenie z *filename*.vsix do *filename*.zip.  
  
2. Skopiuj zawartość pliku zip do katalogu.  
  
3. Usuwanie pliku [Content_types] .xml z katalogu.  
  
4. Edytowanie manifestu VSIX, jak pokazano w poprzedniej procedurze.  
  
5. Dodaj pozostałych plików do projektu Instalatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie za pomocą Instalatora programu Visual Studio](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Przewodnik: Tworzenie akcji niestandardowej](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
