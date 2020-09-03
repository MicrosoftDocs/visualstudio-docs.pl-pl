---
title: Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8fc2a428753e9650bb0dfebdb2bfdfdde10697a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672285"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czy chcesz zapisać parametry połączenia w bieżącym pliku DBML i plikach konfiguracji aplikacji z tymi informacjami poufnymi?  Kliknij przycisk nie, aby zapisać parametry połączenia bez informacji poufnych.

 Podczas pracy z połączeniami danych, które zawierają informacje poufne (hasła zawarte w parametrach połączenia), można zapisać parametry połączenia w pliku DBML projektu i plikach konfiguracji aplikacji z lub bez informacji poufnych.

> [!WARNING]
> Jawne ustawienie właściwości **połączenia** właściwości **ustawień aplikacji** na **Fałsz** spowoduje dodanie hasła do pliku DBML.

### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Aby zapisać parametry połączenia z informacjami poufnymi w ustawieniach aplikacji projektu

- Kliknij przycisk **Yes** (Tak).

     Parametry połączenia są przechowywane jako ustawienia aplikacji. Parametry połączenia zawierają informacje poufne w postaci zwykłego tekstu. Plik DBML nie zawiera informacji poufnych.

### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Aby zapisać parametry połączenia bez informacji poufnych w ustawieniach aplikacji projektu

- Kliknij przycisk **nie**.

     Parametry połączenia są przechowywane jako ustawienia aplikacji, ale hasło nie jest uwzględniane.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
