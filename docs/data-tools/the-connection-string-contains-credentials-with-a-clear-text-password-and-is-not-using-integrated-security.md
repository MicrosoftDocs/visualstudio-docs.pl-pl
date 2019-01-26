---
title: Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 37155efecd7019c0de82d37ee8b071a74a29eea6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966533"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń

Czy chcesz zapisać parametry połączenia w bieżącym pliku DBML i pliki konfiguracyjne aplikacji z tymi informacjami poufnymi?  Kliknij przycisk **nr** można zapisać parametry połączenia bez informacji poufnych.

Podczas pracy z połączeniami danych, zawierające informacje poufne (hasła, które znajdują się w parametrach połączenia), możesz skorzystać z opcji zapisanie parametrów połączenia w pliku DBML projektu i pliku konfiguracji aplikacji z użyciem lub bez poufne informacje.

> [!WARNING]
> Jawne ustawianie **połączenia** właściwości **ustawienia aplikacji** właściwości **False** spowoduje dodanie hasła do pliku DBML.

## <a name="save-options"></a>Opcje zapisywania

- Aby zapisać parametry połączenia z poufnych informacji, wybierz **tak**.

   Parametry połączenia są przechowywane jako ustawienie aplikacji. Parametry połączenia zawierają poufne informacje w postaci zwykłego tekstu. Za pomocą pliku DBML nie zawiera poufne informacje.

- Aby zapisać parametry połączenia bez informacji poufnych, wybierz **nie**.

   Parametry połączenia są przechowywane jako ustawienie aplikacji, ale hasło nie jest dołączony.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)