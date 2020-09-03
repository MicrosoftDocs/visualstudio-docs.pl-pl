---
title: 'CA2210: zestawy powinny mieć prawidłowe silne nazwy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8f800a550717abfabdfb9296fc8f6de49d127d73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548203"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Zestawy powinny mieć prawidłowe silne nazwy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Zestaw nie jest podpisany przy użyciu silnej nazwy, nie można zweryfikować silnej nazwy lub silna nazwa nie będzie prawidłowa bez bieżących ustawień rejestru na komputerze.

## <a name="rule-description"></a>Opis reguły
 Ta reguła pobiera i weryfikuje silną nazwę zestawu. Występuje naruszenie, jeśli którykolwiek z następujących warunków jest spełniony:

- Zestaw nie ma silnej nazwy.

- Zestaw został zmieniony po podpisaniu.

- Zestaw jest podpisany z opóźnieniem.

- Zestaw został niepoprawnie podpisany lub nie można podpisać.

- Zestaw wymaga ustawień rejestru w celu przeprowadzenia weryfikacji. Na przykład narzędzie silnej nazwy (Sn.exe) zostało użyte do pominięcia weryfikacji zestawu.

  Silna nazwa chroni klientów przed nieświadomym ładowaniem zestawu, który został zmieniony. Zestawy bez silnej nazwy nie powinny być wdrażane poza bardzo ograniczonymi scenariuszami. Jeśli użytkownik udostępnia lub dystrybuuje zestawy, które nie są poprawnie podpisane, zestaw może zostać zmieniony, środowisko uruchomieniowe języka wspólnego może nie załadować zestawu lub użytkownik będzie musiał wyłączyć weryfikację na swoim komputerze. Zestaw bez silnej nazwy ma następujące wady:

- Nie można zweryfikować jego pochodzenia.

- Środowisko uruchomieniowe języka wspólnego nie może ostrzegać użytkowników o zmianie zawartości zestawu.

- Nie można go załadować do globalnej pamięci podręcznej zestawów.

  Należy pamiętać, że aby załadować i przeanalizować zestaw z opóźnieniem, należy wyłączyć weryfikację dla zestawu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 **Aby utworzyć plik klucza**

 Użyj jednej z następujących procedur:

- Użyj narzędzia konsolidatora zestawu (Al.exe) dostarczonego przez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zestaw SDK.

- W przypadku [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji 1.0 lub 1.1 należy użyć <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atrybutu lub.

- Dla programu [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Użyj `/keyfile` `/keycontainer` opcji kompilatora lub [/keyfile (Określ klucz lub parę kluczy, aby podpisać zestaw)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) lub [/KEYCONTAINER (Określ kontener kluczy, aby podpisać zestaw)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) opcji konsolidatora w języku C++.

  **Aby podpisać zestaw za pomocą silnej nazwy w programie Visual Studio**

1. W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Otwórz rozwiązanie.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **właściwości.**

3. Kliknij kartę **podpisywanie** i zaznacz pole wyboru **podpisz zestaw** .

4. W obszarze **Wybierz plik klucza o silnej nazwie**wybierz pozycję **Nowy**.

    Zostanie wyświetlone okno **Utwórz klucz o silnej nazwie** .

5. W polu **Nazwa pliku klucza**wpisz nazwę klucza silnej nazwy.

6. Zdecyduj, czy klucz ma być chroniony hasłem, a następnie kliknij przycisk **OK**.

7. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Kompiluj**.

   **Aby podpisać zestaw za pomocą silnej nazwy poza programem Visual Studio**

- Użyj narzędzia silnej nazwy (Sn.exe) dostarczanego przez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zestaw SDK. Aby uzyskać więcej informacji, zobacz [Sn.exe (Narzędzie silnej nazwy)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń tylko ostrzeżenie z tej reguły, jeśli zestaw jest używany w środowisku, w którym manipulowanie zawartością nie jest problemem.

## <a name="see-also"></a>Zobacz też
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Instrukcje: podpisywanie zestawu za pomocą silnej nazwy](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (Narzędzie silnej nazwy)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
