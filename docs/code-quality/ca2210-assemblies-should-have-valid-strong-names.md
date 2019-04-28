---
title: 'CA2210: Zestawy powinny mieć prawidłowe silne nazwy'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e596f2e970df487a31628ab0bd29051172b950e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796682"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Zestawy powinny mieć prawidłowe silne nazwy

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Zestaw jest podpisany silną nazwą, nie można zweryfikować silnej nazwy lub silnej nazwy nie jest prawidłowym bez bieżące ustawienia rejestru komputera.

## <a name="rule-description"></a>Opis reguły

Ta zasada pobiera i weryfikuje silną nazwę zestawu. Naruszenie wystąpi w przypadku spełnienia dowolnego z następujących czynności:

- Zestaw ma silną nazwę.

- Zestaw został zmieniony po zarejestrowaniu się.

- Zestaw jest podpisany z opóźnieniem.

- Zestaw został niepoprawnie podpisany lub podpisywanie nie powiodło się.

- Zestaw wymaga ustawienia rejestru w celu przekazania weryfikacji. Na przykład narzędzie silnych nazw (Sn.exe) został użyty do pominięcia weryfikacji dla zestawu.

Silna nazwa chroni klientów przed nieświadomym ładowaniem zestawu, który został zmieniony. Zestawy bez silnej nazwy nie powinny być wdrażane poza bardzo ograniczonymi scenariuszami. Jeśli użytkownik udostępnia lub dystrybuuje zestawy, które nie są poprawnie podpisane, zestaw może zostać zmieniony, środowisko uruchomieniowe języka wspólnego może nie załadować zestawu lub użytkownik będzie musiał wyłączyć weryfikację na swoim komputerze. Ma to zestaw bez silnej nazwy z następujące wady:

- Nie można zweryfikować jej źródła.

- Środowisko uruchomieniowe języka wspólnego nie ostrzec użytkowników, jeśli zawartość zestawu została zmieniona.

- Nie można załadować do pamięci podręcznej zestawów globalnych.

Należy pamiętać, że można załadować i przeanalizować zestawu podpisanego z opóźnieniem, należy wyłączyć weryfikację zestawu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

### <a name="create-a-key-file"></a>Utwórz plik klucza

Użyj jednej z następujących procedur:

- Narzędzie Assembly Linker (Al.exe) dostarczonych przez .NET Framework SDK.

- .NET Framework w wersji 1.0 lub 1.1, użyj <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> lub <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atrybutu.

- Aby uzyskać [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], użyj jednej `/keyfile` lub `/keycontainer` — opcja kompilatora [/KeyFile (Określ klucz lub parę klucz Aby podpisać zestaw)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) lub  [ /KeyContainer (Określ kontener klucza, aby podpisać zestaw)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) — opcja konsolidatora w języku C++).

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Utwórz zestaw o silnej nazwie w programie Visual Studio

1. W programie Visual Studio Otwórz swoje rozwiązanie.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości.**

3. Kliknij przycisk **podpisywanie** , a następnie wybierz pozycję **Podpisz zestaw** pole wyboru.

4. Z **wybierz plik klucza o silnej nazwie**, wybierz opcję **New**.

   **Utwórz klucz silnej nazwy** oknie zostanie wyświetlona.

5. W **nazwę pliku klucza**, wpisz nazwę dla swojego klucza silnej nazwy.

6. Wybierz, czy klucz jest chroniony hasłem, a następnie kliknij przycisk **OK**.

7. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **kompilacji**.

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Podpisać zestaw silną nazwą poza programem Visual Studio

Narzędzie silnych nazw (Sn.exe) dostarczonego przez .NET Framework SDK. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Tylko Pomijaj ostrzeżeń dla tej reguły, jeśli zestaw jest używany w środowisku, w których naruszeniu zawartość nie jest wymagana.

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [Instrukcje: Podpisywanie zestawu silną nazwą](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool)