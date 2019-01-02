---
title: Tworzenie przenośna profilowania pliki danych z poziomu wiersza polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01b373fbe8a9aa0d7154f03855bb95472edf6b28
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959725"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Tworzenie przenośnych plików danych profilowania z wiersza polecenia
Aby ułatwić udostępnianie danych ułatwia profilowania, można użyć [VSPerfReport](../profiling/vsperfreport.md) narzędzie wiersza polecenia do osadzenia symbole dla przebiegu do profilowania. *Vsp* pliku.  
  
 Możesz również utworzyć wstępnie analizowanych danych profilowania (. *vsps*) plik, który jest mniejszy i jest szybsze ładowanie w środowisku IDE.  
  
> [!NOTE]
>  Upewnij się, że symbol (. *plik PDB*) pliki są dostępne dla **VSPerfReport**. Aby uzyskać więcej informacji, zobacz [jak: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Aby uzyskać informacje o ścieżce do **VSReport**, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Dane profilowania. *vsps* plików nie mogą zostać odfiltrowane.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Aby osadzić symbole dla przebiegu profilowania danych profilowania (. *Vsp*) plików  
  
- W oknie wiersza polecenia wpisz następujące polecenie:  
  
   \<Ścieżka ><strong>VSPerfReport \<</strong> pliku VSP > **packsymbols**  
  
   Domyślnie. *vsps* nazwie z podstawowej nazwy pliku. *Vsp* pliku. Należy określić nazwę alternatywną, za pomocą **dane wyjściowe** opcji.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Aby utworzyć plik danych profilowania podsumowania  
  
- W oknie wiersza polecenia wpisz następujące polecenie:  
  
   \<Ścieżka ><strong>VSPerfReport \<</strong> pliku VSP > **/summaryfile** [**/Output:**\<nazwa pliku >]  
  
   Domyślnie. *vsps* nazwie z podstawowej nazwy pliku. *Vsp* pliku. Należy określić nazwę alternatywną, za pomocą **dane wyjściowe** opcji.