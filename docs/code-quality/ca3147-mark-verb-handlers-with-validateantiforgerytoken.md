---
title: 'CA3147: Oznaczanie procedur obsługi zleceń za pomocą tokenu ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 01b290a4e4656aef079b27ce3abb2a66d7adeb75
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236984"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Oznaczanie procedur obsługi zleceń za pomocą tokenu ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda akcji kontrolera ASP.NET MVC nie jest oznaczona za pomocą [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118))lub atrybut określająca czasownik http, taki jak [HttpGetAttribute](/previous-versions/aspnet/ee470993(v%3dvs.118)) lub [AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Opis reguły

Podczas projektowania kontrolera MVC ASP.NET należy zastanowić się, że zachodzą przypadki fałszerstwa żądań między witrynami. Atakujący sfałszowanie żądań między lokacjami może wysyłać złośliwych żądań od uwierzytelnionego użytkownika do kontrolera MVC ASP.NET. Aby uzyskać więcej informacji, zobacz [XSRF/CSRF zapobieganie w ASP.NET MVC i stronach sieci Web](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Ta reguła sprawdza, czy metody akcji kontrolera MVC ASP.NET są następujące:

- Mają [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/dd492108%28v%3dvs.118%29) i określają dozwolone zlecenia http, bez uwzględniania protokołu HTTP GET.

- Określ jako dozwolone zlecenie HTTP GET.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- W przypadku akcji kontrolera ASP.NET MVC, które obsługują żądania HTTP GET i nie mają potencjalnie szkodliwych efektów ubocznych, Dodaj [HttpGetAttribute](/previous-versions/aspnet/ee470993%28v%3dvs.118%29) do metody.

   Jeśli masz ASP.NETą akcję kontrolera MVC, która obsługuje żądania HTTP GET i ma potencjalnie szkodliwe skutki uboczne, takie jak modyfikowanie poufnych danych, aplikacja jest narażona na ataki fałszerstwa żądań między lokacjami.  Należy ponownie zaprojektować aplikację, tak aby tylko żądania HTTP POST, PUT i DELETE wykonywały poufne operacje.

- W przypadku akcji kontrolera ASP.NET MVC, które obsługują żądania HTTP POST, PUT lub DELETE, Dodaj [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118)) i atrybuty określające dozwolone czasowniki http ([AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29), [HttpPostAttribute](/previous-versions/aspnet/ee264023%28v%3dvs.118%29), [ HttpPutAttribute](/previous-versions/aspnet/ee470909%28v%3dvs.118%29)lub [HttpDeleteAttribute](/previous-versions/aspnet/ee470917%28v%3dvs.118%29)). Ponadto należy wywołać metodę [HtmlHelper. AntiForgeryToken ()](/previous-versions/aspnet/dd504812%28v%3dvs.118%29) z widoku MVC lub strony sieci Web Razor. Aby zapoznać się z przykładem, zobacz temat [Badanie metod edycji i widoku edycji](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły, jeśli:

- Akcja kontrolera ASP.NET MVC nie ma szkodliwych efektów ubocznych.

- Aplikacja weryfikuje token antysfałszowany w inny sposób.

## <a name="validateantiforgerytoken-attribute-example"></a>Przykład atrybutu ValidateAntiForgeryToken

### <a name="violation"></a>Krocz

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Przykład atrybutu narzędzia HttpGet

### <a name="violation"></a>Krocz

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
