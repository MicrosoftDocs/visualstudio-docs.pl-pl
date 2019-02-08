---
title: 'CA2100: Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5387ce65532cb532192191bd67f29cc7af6e28c0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957536"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda ustawia <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> właściwości przy użyciu ciągu, który jest zbudowany z argumentem ciągu do metody.

## <a name="rule-description"></a>Opis reguły

Zasada ta zakłada, że argument ciągu zawiera dane wejściowe użytkownika. Ciąg polecenia SQL zbudowany z danych wejściowych użytkownika jest narażony na ataki przez wstrzyknięcie kodu SQL. W przypadku ataku polegającego na iniekcji SQL złośliwy użytkownik dostarcza dane wejściowe, które zmienia Projekt kwerendy w celu podjęcia próby uszkodzić lub uzyskania nieautoryzowanego dostępu do podstawowej bazy danych. Typowe techniki to m.in. wprowadzanie pojedynczy cudzysłów lub apostrof, czyli Ogranicznik ciągu literału SQL; dwa łączniki, które oznacza Komentarz SQL; i średnikiem, co oznacza, że następujące nowe polecenie. Jeśli dane wejściowe użytkownika musi należeć do zapytania, użyj jednej z następujących pozycji, wymienione w kolejności skuteczności, aby zmniejszyć ryzyko ataków.

- Użyj procedury składowanej.

- Przy użyciu parametrów poleceń sparametryzowanych.

- Weryfikowanie danych wejściowych użytkownika, zarówno dla typu i zawartości, przed utworzeniem ciągu polecenia.

Następujące typy .NET Framework implementują <xref:System.Data.IDbCommand.CommandText%2A> właściwość lub ustaw właściwość przy użyciu argumentu ciągu konstruktorów.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> i <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> i <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> i <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> i <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Należy zauważyć, że zasada ta jest naruszona stosowania metody ToString typu jest jawnie lub niejawnie do konstruowania ciągu zapytania. Oto przykład.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Zostanie naruszona zasada, ponieważ złośliwy użytkownik może zastąpić metodę ToString().

 Również zostanie naruszona zasada niejawnie stosowania ToString.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy użyć sparametryzowanych zapytań.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli tekst polecenia nie zawiera danych podawanych przez użytkownika.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metodę `UnsafeQuery`, który narusza regułę i metody `SaferQuery`, odpowiadającej reguły za pomocą ciągu sparametryzowanego polecenia.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Zobacz także
 [Przegląd zabezpieczeń](/dotnet/framework/data/adonet/security-overview)