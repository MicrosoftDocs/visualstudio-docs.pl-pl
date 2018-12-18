---
title: Wytyczne dotyczące obsługi izolowanych powłoki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a795e5dc71183550e660f8ce7d67f1a41bddbcf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726779"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Wytyczne dotyczące aplikacji Isolated Shell obsługi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas dystrybucji aplikacji powłoki programu Visual Studio, izolowany musi umożliwiać udostępnienia aktualizacji oprogramowania dla aplikacji po jej zainstalowaniu. Aby to zrobić, należy zainstalować aplikację przy użyciu pliku Instalatora Microsoft (MSI). Tego rodzaju instalacji umożliwia aktualizacji oprogramowania firmy Microsoft pozwala na redystrybucję, sieci Web, Pobierz i używane przez klientów bez konieczności interwencji niestandardowych.  
  
## <a name="servicing-requirements"></a>Wymagania dotyczące serwisowania.  
 Możesz zapewnić instalację programu shell w trybie izolowanym Zezwalaj na aktualizacje, upewniając się, że program instalacyjny spełnia następujące kryteria trzy.  
  
### <a name="redistribute-by-using-an-msi"></a>Rozpowszechniać za pomocą Instalatora MSI  
 Aby ponownie dystrybuować aplikację, należy użyć Instalatora MSI, ponieważ Instalator MSI zachowuje tożsamości produktu i upewnia się, że aplikacja ma lokalizacji fizycznej na komputerze klienckim. Moduły scalania (pliki .msm) są oferowane takie gwarancje i nie powinna być używana.  
  
### <a name="accounting-for-custom-actions"></a>Dla akcji niestandardowych  
 Akcje niestandardowe są dyrektywy niestandardowej instalacji w programie Instalatora. Akcje niestandardowe Zmień parametry, takie jak lokalizacje plików, ustawień rejestru, ustawień użytkownika lub inne elementy wymagane do instalacji. Akcje niestandardowe mogą wykonywać operacje na danych w czasie instalacji.  
  
 Gdy używasz akcje niestandardowe w programie instalacyjnym, upewnij się, że akcja niestandardowa co godzinę instalacji muszą mieć odpowiedni akcję niestandardową do Cofnij akcję, jeśli użytkownik odinstaluje aplikację. Twoja instalacja programu kończy się niepowodzeniem zapewnienie odpowiadającego odinstalować akcję niestandardową, usunięcie aplikacji spowoduje zamknięcie ona częściowo zainstalowana.  
  
-   Akcja niestandardowa, która zależy od określonej wersji pliku lub skrót wartości zakończy się niepowodzeniem, gdy aktualizacje oprogramowania, zmiany te wersje lub wartości mieszania. W tym przypadku akcji niestandardowej, należy ręcznie zaktualizować te wartości. Dodatkowe problem występuje, jeśli wersje pliku lub skrót wartości są wspólne dla wersji produktu. Należy unikać tej zależności, jeśli to możliwe.  
  
### <a name="accounting-for-shared-files"></a>Ewidencjonowanie aktywności dla udostępnionych plików  
 Udostępnione pliki takich samych nazwach i są zainstalowane w tej samej lokalizacji, wielu produktów. Te produkty mogą się różnić w wersji i/lub magazynie utrzymywanie jednostki SKU, a produkty mogą współistnieć na danym komputerze. Jednak pliki udostępnione utworzyć obsługi problemów z kilku powodów:  
  
-   Aktualizowanie plików udostępnionych może spowodować problemy ze zgodnością aplikacji, ponieważ aktualizacja do jednej aplikacji mogą ulec zmianie wersji pliku używany przez aplikację drugi, który nie został zaktualizowany. Instalatory dla produktów, które pliki można udostępniać zliczanie odwołań do udostępnionych plików. W związku z tym odinstalowywanie produktu nie wpływa na pliki udostępnione poza zmniejszanie liczby zainstalowanych wystąpień.  
  
-   Instalator Quick Fix Engineering (QFE) zostanie przywrócony do wersji produktów, które Instalator QFE obsługiwanych wersji plików. Ten proces zostanie przerwany potencjalnie aplikacji, które zostało dostarczone zaktualizowanego pliku udostępnionego.

