---
title: 'CA2100: Przejrzyj zapytania SQL pod kątem luk w zabezpieczeniach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e7258ec98937e7ea84773e788234e5a34772e9d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652193"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Należy przejrzeć zapytania SQL w poszukiwaniu luk w zabezpieczeniach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda ustawia właściwość <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> za pomocą ciągu skompilowanego z argumentu ciągu do metody.

## <a name="rule-description"></a>Opis reguły
 Zasada ta zakłada, że argument ciągu zawiera dane wejściowe użytkownika. Ciąg polecenia SQL zbudowany z danych wejściowych użytkownika jest narażony na ataki przez wstrzyknięcie kodu SQL. W przypadku ataku polegającego na iniekcji SQL złośliwy użytkownik wprowadza dane wejściowe, które zmieniają projekt zapytania w próbie uszkodzenia lub uzyskania nieautoryzowanego dostępu do źródłowej bazy danych. Typowe techniki obejmują iniekcję pojedynczego cudzysłowu lub apostrofu, który jest ogranicznikiem ciągu znaków literału SQL; dwie kreski, co oznacza komentarz SQL; i średnik, który wskazuje, że nowe polecenie jest następujące. Jeśli dane wejściowe użytkownika muszą być częścią zapytania, użyj jednego z następujących elementów w kolejności skuteczności, aby zmniejszyć ryzyko ataku.

- Użyj procedury składowanej.

- Użyj sparametryzowanego ciągu polecenia.

- Sprawdź poprawność danych wejściowych użytkownika dla typu i zawartości przed skompilowaniem ciągu polecenia.

  Następujące typy [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] implementują Właściwość <xref:System.Data.IDbCommand.CommandText%2A> lub dostarczają konstruktorów, które ustawiają właściwość przy użyciu argumentu ciągu.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> i <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> i <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> i <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System. Data. SqlServerCe. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) i [System. Data. SqlServerCe. SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> i <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Należy zauważyć, że ta reguła jest naruszona, gdy Metoda ToString typu jest używana jawnie lub niejawnie do konstruowania ciągu zapytania. Oto przykład.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Reguła jest naruszana, ponieważ złośliwy użytkownik może zastąpić metodę ToString ().

 Zasada jest również naruszona, gdy Metoda ToString jest używana niejawnie.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, użyj zapytania parametrycznego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli tekst polecenia nie zawiera żadnych danych wprowadzonych przez użytkownika, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, `UnsafeQuery`, która narusza regułę i metodę `SaferQuery`, która spełnia regułę przy użyciu sparametryzowanego ciągu polecenia.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Przegląd zabezpieczeń](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
