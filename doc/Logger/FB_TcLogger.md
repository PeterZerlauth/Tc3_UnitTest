# FB_TcLogger

**Type:** `FUNCTION BLOCK`
**Source File:** `Logger/FB_TcLogger.TcPOU`

*No documentation found.*

## Methods

### `M_Critical` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Log(E_LogLevel.Critical, Message);
```

---
### `M_Debug` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Log(E_LogLevel.Debug, Message);
```

---
### `M_Error` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Log(E_LogLevel.Error, Message);
```

---
### `M_Info` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Log(E_LogLevel.Info, Message);
```

---
### `M_Log` : `E_LogLevel`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `LogLevel` | `E_LogLevel` |  |

**Implementation:**
```iec
CASE LogLevel OF
	E_LogLevel.Debug:
		IF LogLevel >= stSettings.eLogLevelMinimum AND LogLevel <= stSettings.eLogLevelMaximum THEN
			ADSLOGSTR(ADSLOG_MSGTYPE_STRING OR ADSLOG_MSGTYPE_LOG,'Debug: %s', Message);
		END_IF
		
	E_LogLevel.Info:
		IF LogLevel >= stSettings.eLogLevelMinimum AND LogLevel <= stSettings.eLogLevelMaximum THEN
			ADSLOGSTR(ADSLOG_MSGTYPE_HINT OR ADSLOG_MSGTYPE_LOG,'Info: %s', Message);
		END_IF
		
	E_LogLevel.Warning:
		IF LogLevel >= stSettings.eLogLevelMinimum AND LogLevel <= stSettings.eLogLevelMaximum THEN
			ADSLOGSTR(ADSLOG_MSGTYPE_WARN OR ADSLOG_MSGTYPE_LOG,'Warning: %s', Message);
		END_IF
		
	E_LogLevel.Error:
		IF LogLevel >= stSettings.eLogLevelMinimum AND LogLevel <= stSettings.eLogLevelMaximum THEN
			ADSLOGSTR(ADSLOG_MSGTYPE_ERROR OR ADSLOG_MSGTYPE_LOG,'Error: %s', Message);
		END_IF
		
	E_LogLevel.Critical:
		IF LogLevel >= stSettings.eLogLevelMinimum AND LogLevel <= stSettings.eLogLevelMaximum THEN
			ADSLOGSTR(ADSLOG_MSGTYPE_ERROR OR ADSLOG_MSGTYPE_LOG,'Critical: %s', Message);
		END_IF
		
END_CASE
```

---
### `M_Warning` : `STRING`
*No documentation found.*
**Inputs:**
| Name | Type | Description |
| --- | --- | --- |
| `Message` | `STRING` |  |

**Implementation:**
```iec
M_Log(E_LogLevel.Warning, Message);
```

---

## Properties

### `P_Settings`
*No documentation found.*

**Get Implementation:**
```iec
P_Settings ref= stSettings;
```
**Set Implementation:**
```iec
P_Settings ref= stSettings;
```

---

## Implementation
```iec
// https://peterzerlauth.com/
```
