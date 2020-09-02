---
title: 'Instrukcje: ograniczanie instrumentacji do określonych bibliotek DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc2fe8e6f9b0ed1e6970943ab5eedf1b62eb961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807722"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Porady: ograniczanie instrumentacji do określonych bibliotek DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z metody profilowania instrumentacji, można ograniczyć zbieranie danych profilowania do co najmniej jednej biblioteki DLL w aplikacji. Aby profilować co najmniej jedną bibliotekę DLL w aplikacji, należy utworzyć sesję wydajności, która zawiera pliki. dll jako elementy docelowe. Możesz określić biblioteki DLL, które chcesz profilować jako projekty w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązaniu lub jako niezależne pliki binarne.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Aby ograniczyć instrumentację do określonych bibliotek DLL w rozwiązaniu programu Visual Studio  
  
1. Otwórz rozwiązanie, które zawiera plik DLL w programie [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
2. W menu **Analizuj** wybierz pozycję **Uruchom Kreatora wydajności**.  
  
3. Wybierz **instrumentację** jako metodę profilowania, a następnie kliknij przycisk **dalej**.  
  
4. Z **następujących dostępnych elementów docelowych chcesz profilować?** wybierz nazwę projektu. dll, a następnie kliknij przycisk **dalej**.  
  
5. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i wyświetlić nową sesję wydajności w oknie **Eksplorator wydajności** .  
  
6. Kliknij prawym przyciskiem myszy element **docelowy** , a następnie wybierz polecenie **Dodaj projekt docelowy**.  
  
7. Z listy **Dodaj projekt docelowy** wybierz projekt wykonywalny, który ma być używany do korzystania z biblioteki DLL.  
  
     Opcjonalny. Możesz dodać wszystkie projekty DLL, które chcesz profilować.  
  
8. Aby uniemożliwić zbieranie danych dla dodanego projektu, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wyczyść pole wyboru **instrument** .  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Aby określić określone biblioteki DLL do profilowania jako niezależne pliki binarne  
  
1. Otwórz plik [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2. W menu **Analizuj** wybierz pozycję **Uruchom Kreatora wydajności**.  
  
3. Z **następujących dostępnych elementów docelowych chcesz profilować**, wybierz **profil biblioteka dołączana dynamicznie (. DLL)** , a następnie kliknij przycisk **dalej**.  
  
4. Na drugiej stronie kreatora wykonaj następujące czynności:  
  
    - Wpisz ścieżkę i nazwę pliku dll, który ma być profilem w **ścieżce dll**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w oknie dialogowym **biblioteka dołączana dynamicznie do profilowania** . Należy pamiętać, że należy określić kopię pliku dll, który będzie uruchamiany przez wybrany plik wykonywalny (exe).  
  
    - Wpisz ścieżkę i nazwę pliku wykonywalnego (exe), który będzie wykonywał plik. dll w **ścieżce pliku wykonywalnego**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w oknie dialogowym **plik wykonywalny do uruchomienia** .  
  
    - Opcjonalny. Wpisz wszystkie argumenty wiersza polecenia, które chcesz przekazać do pliku wykonywalnego w **argumentach wiersza polecenia**. W razie potrzeby określ katalog roboczy aplikacji w **katalogu roboczym**.  
  
    - Kliknij przycisk **Dalej**.  
  
5. Wybierz **instrumentację** jako metodę profilowania, a następnie kliknij przycisk **dalej**.  
  
6. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i wyświetlić nową sesję wydajności w oknie **Eksplorator wydajności** .  
  
7. Opcjonalny. Aby dodać więcej plików DLL, kliknij prawym przyciskiem myszy **obiekt docelowy** , a następnie wybierz **Dodaj docelowy plik binarny**. Wybierz pliki z okna dialogowego **Dodaj docelowy plik binarny** .  
  
    > [!NOTE]
    > Nie określaj pliku wykonywalnego (exe), który wykonuje biblioteki DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
