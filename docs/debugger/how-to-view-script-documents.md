---
title: 'Porady: wyświetlanie dokumentów skryptu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bfa273f98cebdf61f865e03a02c9b2d5f22bfa9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474732"
---
# <a name="how-to-view-script-documents"></a>Porady: wyświetlanie dokumentów skryptu
W starszych wersjach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], w oknie Eksploratora skryptu pojawił się wygenerowanych ze skryptu po stronie serwera plików skryptu po stronie klienta. Okno Eksploratora skryptu często został ukryty, dzięki czemu dostępności skryptu po stronie klienta nie jest zawsze widoczne.  
  
 W [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], wygenerowanych ze skryptu po stronie serwera plików skryptu po stronie klienta są wyświetlane w Eksploratorze rozwiązań, które jest domyślnie widoczne. Okno Eksploratora skrypt został wyeliminowany.  
  
 Pliki skryptów po stronie klienta są widoczne tylko wtedy, gdy są w trybie debugowania lub w trybie przerwania. Pojawią się one w **dokumentów skryptu** węzła.  
  
 Pliki skryptów po stronie serwera są zawsze widoczne. Pojawią się one w  **\<Pathname witryny sieci Web >** węzła. Nazwa węzła podobny w tym przykładzie: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie serwera  
  
1.  W **Eksploratora rozwiązań**, otwórz  **\<Pathname witryny sieci Web >** węzła.  
  
2.  Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.  
  
     Otwiera plik skryptu po stronie serwera w oknie źródła.  
  
### <a name="to-view-a-client-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie klienta  
  
1.  W **Eksploratora rozwiązań**, otwórz **dokumentów skryptu** węzła.  
  
2.  Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.  
  
     Otwiera plik skryptu po stronie klienta w oknie źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)