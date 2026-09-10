# File: `cogs/gen_img.py`

## Overview
Core module for gen_img.py.

## Classes

### `ImageGenerationCog`
Class representing ImageGenerationCog.

- **Attributes**:
  - `bot` (`Any`): Instance attribute.
  - `lang_manager` (`Optional[LanguageManager]`): Instance attribute.
  - `session` (`Any`): Instance attribute.
  - `tokens` (`Any`): Instance attribute.
  - `client` (`Any`): Instance attribute.
  - `model_id` (`Any`): Instance attribute.
  - `conversation_history` (`Dict[int, List[Dict]]`): Instance attribute.
  - `logger` (`Any`): Instance attribute.

- **Methods**:
  - `__init__(self, bot: Any) -> Any`: Method __init__.
  - `cog_load(self) -> Any`: Initialize the language manager when the cog is loaded
  - `_get_conversation_history(self, channel_id: int) -> List[Dict]`: Get the conversation history for a specific channel
  - `_update_conversation_history(self, channel_id: int, role: str, content: str, images: Optional[List[Image.Image]]) -> Any`: Update the conversation history
  - `_generate_image_logic(self, prompt: str, guild_id: str, channel_id: int, input_images: Optional[List[Image.Image]], channel: Optional[discord.TextChannel]) -> Dict`: Core image generation logic.
  - `generate_image_command(self, interaction: discord.Interaction, prompt: str) -> Any`: Method generate_image_command.
  - `_image_to_base64(self, image: Image.Image) -> str`: Convert a PIL Image to a base64-encoded string
  - `generate_with_gemini(self, prompt: str, image_input: List[Image.Image], dialogue_history: List[Dict]) -> tuple[Optional[io.BytesIO], Optional[str]]`: Generate images using the Gemini API
  - `generate_with_local_model(self, channel: Any, prompt: str, n_steps: int, message_to_edit: discord.Message, guild_id: str) -> Any`: Generate images using a local model
  - `cog_unload(self) -> Any`: 清理資源

## Functions

### `setup(bot: Any) -> Any`
Function setup.
