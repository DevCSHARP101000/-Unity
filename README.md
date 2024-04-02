# using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Rendering;

public class PlayerMove : MonoBehaviour
{
    public float MoveSpeed;

    private float horizontal;
    private float vertical;

    private float gravity = 9.8f;
    public float JumpSpeed = 15f;

    public CharacterController PlayerController;

    Vector3 Player_Move;

    void Update()
    {        
        if (PlayerController.isGrounded)
        {
            horizontal = Input.GetAxis("Horizontal");
            vertical = Input.GetAxis("Vertical");

            
            Player_Move = (transform.forward * vertical + transform.right * horizontal) * MoveSpeed;

            if (Input.GetAxis("Jump") == 1)
            {
                Player_Move.y = Player_Move.y + JumpSpeed;
            }
        }

     
        Player_Move.y = Player_Move.y - gravity * Time.deltaTime;


        PlayerController.Move(Player_Move * Time.deltaTime);

    }
}
