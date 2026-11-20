# SigmaOS-advancement Component Wiki

## Overview
SigmaOS-advancement provides achievement progression and skill tree management for the SigmaOS operating system. It demonstrates the gamification subsystem and skill development within the SigmaOS ecosystem, following the principles of clear abstraction and deterministic advancement initialization.

## Principles
- Single Responsibility
- Advancement Abstraction
- Fail-Fast on Advancement Initialization Errors
- Deterministic Advancement Setup
- Clear Abstraction Over Advancement APIs
- Composition over Inheritance for advancement extensions

## Architecture
SigmaOS-advancement follows an advancement pattern:
- **Advancement Core**: Provides skill tree management, progression tracking, and milestone detection
- **Skill Management**: Supports skill acquisition, leveling up, and ability unlocking
- **Progress Tracking**: Manages user progress across skill trees and experience accumulation
- **Error Handling**: Fail-fast on invalid advancement configurations or unsupported skill types

## API
The component provides the following public APIs:
- `advancement::unlock(skill_id)` - Unlock a skill by ID
- `advancement::progress(user)` - Get user progression across all skill trees
- `advancement::milestone::check(user)` - Check for newly unlocked milestones
- `advancement::tree::structure()` - Get the complete skill tree structure
- Error types for advancement failure scenarios or unsupported skill types

## Test Structure (Arrange-Act-ASSERT)
All tests follow the AAA pattern:
1. **Arrange**: Set up test environment with specific advancement configuration
2. **Act**: Execute the code under test (skill unlock, progression check)
3. **Assert**: Verify the expected advancement results

Example:
```rust
#[test]
fn test_advancement_unlock_aaa() {
    // Arrange
    let skill_id = "combat-basics";
    
    // Act
    let result = advancement::unlock(skill_id);
    
    // Assert
    assert!(result.is_ok());
    assert!(advancement::progress().has_skill(skill_id));
}
```

## Development
- Follows Rust best practices with `#![forbid(unsafe_code)]`
- Advancement initialization is best-effort; gracefully degrades on unsupported configurations
- Comprehensive error types for all advancement failure scenarios
- Unit tests provided for skill management and progression tracking
- Integration tests for full advancement system with actual skill development

## TODO
- Add support for additional skill types and ability categories
- Expand progression tracking (experience points, prestige system, skill synergies)
- Add milestone detection and notification features
- Create integration tests with actual skill development systems
- Implement skill persistence and cross-user progression features