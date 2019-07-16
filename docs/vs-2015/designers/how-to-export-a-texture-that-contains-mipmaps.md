---
title: 'Instrukcje: Eksportowanie tekstury zawierającej mipmapy | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f525f4b31a3535f6ea7b89d0443402240365cc7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159437"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Instrukcje: Eksportowanie tekstury zawierającej mipmapy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Potok zawartości obrazu może generować mipmapy z obrazu źródłowego w ramach fazy kompilacji projektu. Jeśli nie trzeba ręcznie określać zawartości obrazu każdego poziomu MIP — co możesz zrobić, aby uzyskać pewne efekty — Generowanie mipmap w czasie kompilacji zapewnia, że zawartość mipmappingu nigdy nie stanie się poza synchronizacji i eliminuje koszty wydajności wytwarzania mipmap w czasie wykonywania.  
  
 Ten dokument przedstawia te działania:  
  
- Konfigurowanie obrazu źródłowego, który ma być przetwarzana przez potok zawartości obrazu.  
  
- Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap.  
  
## <a name="exporting-mipmaps"></a>Eksportowanie Mipmap  
 Mipmapping zapewnia automatyczne ekranowego poziom szczegółów wypełniający dla teksturowanych powierzchni w grze lub aplikacji 3D. Zwiększa wydajność renderowania gry lub aplikacji poprzez wstępnie obliczenie wersji tekstury, aby cała Tekstura nie musi być próbkowana w dół każdorazowo, gdy jest próbkowana.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować teksturę, która ma mipmapy  
  
1. Rozpocznij od podstawowej tekstury. Załaduj istniejący pliku obrazu lub utwórz je, zgodnie z opisem w [jak: Tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać mipmapy, określ teksturę, która ma szerokość i wysokość, które są tego samego przekazu dwa, na przykład 64 x 64, 256 x 256 lub 512 x 512.  
  
2. Skonfigurować pliku tekstury, który został utworzony, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla utworzonego właśnie pliku tekstury, a następnie wybierz **właściwości**. Na **właściwości konfiguracji**, **ogólne** ustaw **typu elementu** właściwości **potok zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **Wyłącz z kompilacji** ustawiono **nie**, a następnie wybierz  **Zastosuj** przycisku. **Potok zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.  
  
3. Konfigurowanie potoku zawartości obrazu, aby nie generować mipmap. Na **właściwości konfiguracji**, **potok zawartości obrazu**, **ogólne** ustaw **Generuj Mips** właściwość **Tak (/ generatemips)** .  
  
4. Wybierz **OK** przycisku.  
  
   Podczas budowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś, włącznie z poziomami MIP, a wynik jest kopiowany do katalogu wyjściowego projektu.
