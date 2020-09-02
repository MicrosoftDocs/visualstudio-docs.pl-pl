---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471583"
---
- Zamiast tego Użyj bezpiecznego serializatora i **nie Zezwalaj osobie atakującej na określenie dowolnego typu do deserializacji**. Aby uzyskać więcej informacji, zobacz [preferowane alternatywy](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).
- Przekształć dane serializowane. Po serializacji należy kryptograficznie podpisywać serializowane dane. Przed deserializacji Sprawdź poprawność podpisu kryptograficznego. Ochrona klucza kryptograficznego przed ujawnieniem i projektowaniem na potrzeby rotacji kluczy.
- Ta opcja sprawia, że kod narażony na ataki typu "odmowa usługi" i możliwe ataki zdalnego wykonywania kodu w przyszłości. Aby uzyskać więcej informacji, zobacz [Przewodnik po zabezpieczeniach BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide). Ogranicz typy deserializowane. Implementowanie niestandardowego <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> . Przed deserializacji należy ustawić `Binder` Właściwość na wystąpienie niestandardowe <xref:System.Runtime.Serialization.SerializationBinder> we wszystkich ścieżkach kodu. W przypadku przesłoniętej <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody, jeśli typ jest nieoczekiwany, Zgłoś wyjątek, aby zatrzymać deserializacji.
