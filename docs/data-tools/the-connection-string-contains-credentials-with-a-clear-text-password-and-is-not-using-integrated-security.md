---
title: Parametry połączenia zawierają hasło
description: Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1ce11b59ad7f38de4c71fa13371da16225b5b843
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858413"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń

Czy chcesz zapisać parametry połączenia w bieżącym pliku DBML i plikach konfiguracji aplikacji z tymi informacjami poufnymi?  Kliknij przycisk **nie** , aby zapisać parametry połączenia bez informacji poufnych.

Podczas pracy z połączeniami danych, które zawierają informacje poufne (hasła zawarte w parametrach połączenia), można zapisać parametry połączenia w pliku DBML projektu i plikach konfiguracji aplikacji z lub bez informacji poufnych.

> [!WARNING]
> Jawne ustawienie właściwości **połączenia** właściwości **ustawień aplikacji** na **Fałsz** spowoduje dodanie hasła do pliku DBML.

## <a name="save-options"></a>Opcje zapisywania

- Aby zapisać parametry połączenia z informacjami poufnymi, wybierz opcję **tak**.

   Parametry połączenia są przechowywane jako ustawienia aplikacji. Parametry połączenia zawierają informacje poufne w postaci zwykłego tekstu. Plik DBML nie zawiera informacji poufnych.

- Aby zapisać parametry połączenia bez informacji poufnych, wybierz pozycję **nie**.

   Parametry połączenia są przechowywane jako ustawienia aplikacji, ale hasło nie jest uwzględniane.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
