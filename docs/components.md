# Components

AIRS components are protocol-level render units. They describe what should be presented, not exactly how the final UI must look.

## Initial Component Types

| Type | Use |
| --- | --- |
| `summary_card` | Short task summary or result summary. |
| `option_card` | Selectable option in a task. |
| `detail_panel` | Detailed view of one item. |
| `form` | Structured user input. |
| `field` | Single value or input field. |
| `list` | Ordered or grouped items. |
| `media` | Image, video, audio, or streaming content. |
| `permission_prompt` | Runtime-controlled permission or confirmation UI. |
| `error_message` | Recoverable error state. |
| `action_bar` | Group of available actions. |

## Component Requirements

Each component requires:

- `id`
- `type`

Recommended fields:

- `title`
- `subtitle`
- `content`
- `fields`
- `items`
- `actions`
- `source`
- `risk_level`

## Runtime Mapping

An AIRS Runtime can map the same component to different platform UI patterns.

For example, an `option_card` may become:

- A card on desktop
- A compact row on mobile
- A voice option in a voice-first interface
- A focusable panel on a TV display

The component semantics should remain stable even when presentation changes.
