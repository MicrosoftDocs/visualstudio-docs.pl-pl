---
title: Przygotowywanie rozszerzeń wdrożenia Instalator Windows | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694593"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie można użyć pakietu Instalator Windows (MSI) do wdrożenia pakietu VSIX. Można jednak wyodrębnić zawartość pakietu VSIX dla wdrożenia MSI. W tym dokumencie przedstawiono sposób przygotowania projektu, którego domyślne dane wyjściowe są pakietem VSIX do uwzględnienia w projekcie instalacji.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Przygotowywanie projektu rozszerzenia do wdrożenia Instalator Windows  
 Wykonaj te kroki w nowych projektach rozszerzeń przed dodaniem do projektu instalacji.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Aby przygotować projekt rozszerzenia dla wdrożenia Instalator Windows  
  
1. Utwórz składnik pakietu VSPackage, MEF, Edytor definiowania układu lub inny typ projektu rozszerzalności, który zawiera manifest VSIX.  
  
2. Otwórz manifest VSIX w edytorze kodu.  
  
3. Dla elementu InstalledByMsi manifestu VSIX ustaw wartość `true` . Aby uzyskać więcej informacji na temat manifestu VSIX, zobacz [odwołanie do schematu rozszerzenia vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Zapobiega to próbie zainstalowania składnika przez Instalatora VSIX.  
  
4. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie kliknij pozycję **Właściwości**.  
  
5. Wybierz kartę **VSIX** .  
  
6. Zaznacz pole wyboru **Kopiuj zawartość VSIX do następującej lokalizacji** i wpisz ścieżkę do lokalizacji, w której projekt instalacyjny będzie pobierał pliki.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Wyodrębnianie plików z istniejącego pakietu VSIX  
 Wykonaj następujące kroki, aby dodać zawartość istniejącego pakietu VSIX do projektu konfiguracji, gdy nie masz plików źródłowych.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Aby wyodrębnić pliki z istniejącego pakietu VSIX  
  
1. Zmień nazwę. Plik VSIX zawierający rozszerzenie z *pliku filename*. VSIX do *filename*. zip.  
  
2. Skopiuj zawartość pliku zip do katalogu.  
  
3. Usuń plik [Content_types]. XML z katalogu.  
  
4. Edytuj manifest VSIX, jak pokazano w poprzedniej procedurze.  
  
5. Dodaj pozostałe pliki do projektu Instalatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrożenie Instalator programu Visual Studio](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Przewodnik: Tworzenie akcji niestandardowej](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
