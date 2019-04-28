---
title: Parametry połączenia zawierają poświadczenia z hasła w postaci zwykłego tekstu, a nie korzysta ze zintegrowanych zabezpieczeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3b75c4e7cf1b1d0374c9ff648861e049aca988c4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424958"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czy chcesz zapisać parametry połączenia w bieżącym pliku DBML i pliki konfiguracyjne aplikacji z tymi informacjami poufnymi?  Kliknij przycisk nie, aby zapisać parametry połączenia bez informacji poufnych.  
  
 Podczas pracy z połączeniami danych, zawierające informacje poufne (hasła, które znajdują się w parametrach połączenia), możesz skorzystać z opcji zapisanie parametrów połączenia w pliku DBML projektu i pliku konfiguracji aplikacji z użyciem lub bez poufne informacje.  
  
> [!WARNING]
> Jawne ustawianie **połączenia** właściwości **ustawienia aplikacji** właściwości **False** spowoduje dodanie hasła do pliku DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Aby zapisać parametry połączenia z poufnych informacji w ustawieniach aplikacji projektu  
  
- Kliknij przycisk **Tak**.  
  
     Parametry połączenia są przechowywane jako ustawienie aplikacji. Parametry połączenia zawierają poufne informacje w postaci zwykłego tekstu. Za pomocą pliku DBML nie zawiera poufne informacje.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Aby zapisać parametry połączenia bez informacji poufnych w ustawieniach aplikacji projektu  
  
- Kliknij przycisk **nie**.  
  
     Parametry połączenia są przechowywane jako ustawienie aplikacji, ale hasło nie jest dołączony.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
